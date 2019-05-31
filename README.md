# Copper Developer API

The Copper Web API allows you to access and build your own applications that interact with Copper in more complex ways than the integrations we provide out of the box.

The Copper Developer API ("Dev API") provides a RESTful interface with JSON-formatted responses to access most Copper resources. We are continuously working on expanding our API functionality, so stay tuned!

Authentication
===================
The Dev API uses a token based authentication. You have to include the token in the header of every request, along with the email address of the user who generated the token. Each Copper user can generate API keys and can have multiple valid tokens at the same time. Admins can see all user generated tokens.

To generate an API token, in the Copper web app go to System settings > API Keys and click the 'CREATE A KEY' button. Copper allows you to label each key for its unique purpose. You'll need to generate an API key to make an API Request.

Requests
========
**Encryption**

All requests must be sent using HTTPS with TLS 1.2 or higher. Please make sure your developer tools support this version of TLS as older versions or SSL are not supported for security reasons.

**Headers**

All Copper API calls must include the following headers to authenticate the request:

|       Key        |            Value             |
| ---------------- | ---------------------------- |
| X-PW-AccessToken | _API Key_                    |
| X-PW-Application | "developer_api"              |
| X-PW-UserEmail   | _Email address of token owner_ |
| Content-Type     | "application/json"           |

**Body**

For PUT or POST requests (e.g. create, update, search), the request parameters must be provided as JSON in the request body.

**Rate limits**

All API calls are limited to 600 requests every 10 minutes. There is also a burst mode limit of 36 requests every 6 seconds that takes precedence over the regular API rate limit. Once either limit has been reached, calls will return and error with status code 429. This rate limit is evaluated on rolling 6 second and 10 minute windows, respectively.

Responses
=========

Responses use the customary [HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes), with the most typical ones being:

|          Code          |        Meaning        |
| ---------------------- | --------------------- |
| *Successful Responses* |                       |
| 200                    | OK                    |
| *Error Responses*      |                       |
| 400                    | Bad Request           |
| 401                    | Unauthorized          |
| 429                    | Too many requests     |
| 500                    | Internal Server Error |

Each of the entities in the Dev API (Leads, People, etc.) has a '/search' endpoint. For requests sent to '/search' endpoints, the response header contains a field called 'X-PW-TOTAL'. This value represents an upper bound of the total number of records returned in the search query. It allows the developer to estimate roughly how long it would take to extract the data when the results are paginated (See Paginating Search Results section).

Search
======================

**Search by Phone Number**

There are two types of phone number search, fuzzy and partial. The difference is in the way the input is permuted prior to search. In general, fuzzy search returns more results, but partial search returns results that are closer to what the user entered. Let's illustrate from an example. Suppose the user enters "408-555-1234". In either search, non-numeric characters are stripped first.

Partial Search: "4085551234" is searched in the database for all records that have phone numbers that end in "4085551234". This includes entities with phone numbers such as "4085551234", "1-4085551234", "123-4085551234", etc.

Fuzzy Search: "4085551234" is permuted first by stripping 1-6 digits from the beginning of the sequence. If the resulting sequence is less than 6 digits long, it is dropped from the search. In this case, the search string set is "4085551234", "085551234", "85551234", "5551234", "551234". Any records in the database where the phone number ends in the string set is returned. The query results form fuzzy match includes results from the partial search and many more ambiguous results. For example, records with phone number such as "5105551234" would also be returned.

To designate the type of phone number search, specify the "match" field when entering the phone number in the search request body. E.g.,

{ "phone_number": { "value": "5551234", "match": "partial" } }

Match scheme is partial if the input string is 6 digits or fewer. For an input string 7 digits or more, the default behavior is fuzzy search if a match scheme is not specified.

Paginating search results
======================

Our /search endpoints return multiple records per response. How many records are included in a single response (=page size) is determined by an optional search parameter called "page_size". The default value for "page_size" is 20, and its value can be set to any integer between 1 and 200. When the search criteria match more records than what fits on a single page then you have to paginate the search results using one of the following strategies in order to get all the records that match your search.

Strategy 1: Calculate the number of pages
---------------------------

Every response from a /search endpoint has a field in the response header called 'X-PW-TOTAL'. It shows an upper bound of the total number of records that match the search criteria.


To calculate the number of pages to cycle thru, divide the total number of records by the page size. For the sake of example, let's assume that the page size is 200 and the total number of records is 775. The number of pages is 775/200 = 3.875 which rounded up to the nearest integer gives us 4 pages.


Now, to cycle thru the pages we need to set the "page_number" parameter in the request to 1 initially, and then send additional requests for the subsequent pages.


The request header will look like this:


_For the first page_


{

...

"page_size": 200,

"page_number": 1

...

}


_For the second page_

{

...

"page_size": 200,

"page_number": 2

...

}

and so on.

This strategy has one caveat; if records are added/modified in the system between the time when the header field is evaluated and when the actual pages are requested then those records may be included or omitted in/from the results incorrectly.

Strategy 2: Count the records on each page
------------------
In this scenario, we send a search request and specify the first page, by setting "page_number" to 1. Then use a logic that performs the following evaluation on the response.


1. Count the number of records in the response
2. Check if the record count equals the page_size
3. a. If the record is less than the page size then we are on the last page and we can stop paginating
3. b. If the record count equals the page size then increase "page_size" by one, send another request and start over with this evaluation logic.


Using the same example as above, with a page size of 200 and 775 total records the evaluation would go down as follows

_Page 1_

{

...

"page_size": 200,

"page_number": 1

...

}

The response will have 200 records which equals the page size, so let's continue requesting.

_Page 2_

{

...

"page_size": 200,

"page_number": 2

...

}

The response will have 200 records which equals the page size, so let's continue requesting. The 3rd page will have identical results.

_Page 4 (last page)_

{

...

"page_size": 200,

"page_number": 4

...

}

The response will have 175 records, which is LESS than the page size, which tells us we are on the last page and we can stop paginating.

Remember to sort you search results!
-------------------
It is highly recommended that you sort the results you get back from a /search endpoint. This ensures that records are returned in a consistent fashion across requests. One common sorting scenario is to sort records by the date they were last updated, in a descending order. For this sorting please add the following parameters to the search request:

{

...

"sort_by": "date_modified",

"sort_direction": "desc"

...

}


Best practices
==============
**Date formats**

Date formats are in Unix Timestamp format and values are set and returned as 10 digit long integers (For example {"date_created": 1483988828}). There are a few notable exceptions, however. The "close_date" on Opportunities, Task Due Dates and Reminder dates, and custom date fields use an ISO "mm/dd/yyyy" format for setting and returning date values.


**The API respects Team Permissions**

A user's access to records in Copper may be restricted by Team Permission settings. The Dev API respects team permissions. It is recommended to use the API credentials of an admin user when using the Dev API because Admins have unrestricted data access.

**Create a Developer User**

If you use the Dev API to create records in Copper, it is advisable to create a separate (non-personal) user just for integration purposes. Generate API credentials for this user and use those for integration. This way records created thru the Dev API will be owned by this integration user and can be filtered accordingly.

**Entity ID scopes**

Unique identifiers are unique within the scope of a single resource type. For example, a given identifier for a Lead will never be assigned to a different Lead, but a different resource such as a Person could use the same identifier.

**File Upload**

Currently, the Developer API does not allow for file uploads. There is a workaround available.

1. Create a custom URL field.
2. Upload your file to Google Drive.
3. Push the created file link into your Copper custom URL field.

Embedded Apps
===================
Embedded Integrations lets you easily display an integration you've built in the Copper web app. [Working with our SDK](https://docs.copper.com/pw-app-sdk/), you can create and embed your own app in Copper in just a few clicks. To join the beta, click [here](https://docs.google.com/forms/d/1tEgGLqAeYQ2PFmkaiwGEBRNGcpDBrK7zKvd2XXtqoIw/viewform?edit_requested=true).

For more info on embedded apps, please go [here](https://support.copper.com/hc/en-us/articles/360001624708-Working-with-Embedded-Integrations-BETA-).

Appendix
============================
**Categories**

When creating or updating entities such as leads or people, there are fields where value and category can be specified. These fields include email, phone, social, and website. Below are the valid categories for each of these fields.

|  Field    |  Categories                                                                                   |
|-----------|-----------------------------------------------------------------------------------------------|
|  Email    |  work, personal, other                                                                        |
|  Phone    |  mobile, work, home, other                                                                    |
|  Social   |  linkedin, twitter, googleplus, facebook, youtube, quora, foursquare, klout, gravatar, other  |
|  Website  |  work, personal, other                                                                        |

Getting Support
============================
For code samples, please visit [Code Samples](https://support.copper.com/hc/en-us/articles/115000816826-Code-samples-and-tips).

For API questions and support, please [Submit a request](https://support.prosperworks.com/hc/en-us/requests/new) or post your question in our [Developer Forum](https://support.prosperworks.com/hc/en-us/community/topics/201113143-ProsperWorks-API-Developer-Forum).