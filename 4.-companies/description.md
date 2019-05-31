# 4. Companies

A Company is an organization with which you communicate. The Companies API allows you to create, view, delete and update your Companies. You can retrieve individual Companies, list all Companies, or use search filters to view subsets of your Companies.

**Company Properties**

| Field | Type | Details |
| :--- | :--- | :--- |
| id | number | Unique identifier for the Company. |
| name\* | string | The name of the Company. |
| address | address | An encapsulation of the Company's street, city, state, postal code, and country. |
| assignee\_id | number | Unique identifier of the User that will be the owner of the Company. |
| contact\_type\_id | number | The unique identifier of the Contact Type of the Company. |
| details | string | Description of the Company. |
| email\_domain | string | The domain to which email addresses for the Company belong. |
| phone\_numbers\[\] | list | An array of phone numbers belonging to the Company. |
| phone\_numbers\[\].number | string | A phone number. |
| phone\_numbers\[\].category | string | The category of the phone number. |
| socials\[\] | list | An array of social profiles belonging to the Company. |
| socials\[\].url | string | The URL of a social profile. |
| socials\[\].category | string | The category of the social profile. |
| tags | list | An array of the tags associated with the Company, represented as strings. |
| websites\[\] | list | An array of websites belonging to the Company. |
| websites\[\].url | string | The URL of a website. |
| websites\[\].category | string | The category of the website. |
| date\_created | number | A Unix timestamp representing the time at which this Company was created. |
| date\_modified | number | A Unix timestamp representing the time at which this Company was last modified. |
| custom\_fields\[\] | list | An array of custom field values belonging to the Company. |
| custom\_fields\[\].custom\_field\_definition\_id | number | The id of the Custom Field Definition for which this Custom Field stores a value. |
| custom\_fields\[\].value | mixed | The value \(number, string, option id, or timestamp\) of this Custom Field. |
| \* indicates a required field |  |  |

_Please note that_ _**email domain is a unique key**_ _for Companies and no two records can have the same domain name. If you try to create a new Company with an existing email domain, then your request will fail._

## Fetch a Company by ID

undefined

`GET {{base_url}}/companies/{{example_company_id}}`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Example Responses

* Company

200: OK

```javascript
{"id":9607580,"name":"Dunder Mifflin (sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"contact_type_id":null,"details":"Keywords: Dunder Mifflin, Dunder Mifflin Infinity, Dunder Mifflin Paper, Dunder Mifflin Scranton, Dunder-mifflin, Dunder-mifflin Paper, Dunder-mifflin Scranton, Dundermifflin, NBC, NBC.com, Office 360, Ryan Howard, Scranton Office Supplies, The Office 360, The Office Tv, The Office Tv Series, The Office Tv Show","email_domain":"dundermifflin.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"},{"url":"https://www.nbcstore.com/shop-by-show/the-office.html?shop_by_theme=7","category":"work"},{"url":"http://dundermifflin.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1489018922}
```

## Create a New Company

undefined

`POST {{base_url}}/companies`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

```text
{
  "name":"Demo Company",
  "address": {
       "street": "123 Main Street",
    "city": "Savannah",
    "state": "Georgia",
    "postal_code": "31410", 
    "country": "United States"
  },
  "email_domain":"democompany.com",
  "details":"This is a demo company",
  "phone_numbers": [
    {
    "number":"415-123-45678",
    "category":"work"
    }
  ]
}
```

### Example Responses

* create company

200: OK

```javascript
{"id":13358412,"name":"Demo Company","address":{"street":"123 Main St","city":"San Francisco","state":"CA","postal_code":"94105","country":null},"assignee_id":null,"contact_type_id":null,"details":"This is a demo company","email_domain":"democompany.com","phone_numbers":[{"number":"415-123-45678","category":"work"}],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1496707930,"date_modified":1496707930}
```

## Update a Company

Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

`PUT {{base_url}}/companies/{{example_company_id}}`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

```text
{
  "details":"This is an update"
}
```

### Example Responses

* Update Company

200: OK

```javascript
{"id":9607580,"name":"Dunder Mifflin (sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"contact_type_id":null,"details":"This is an update","email_domain":"dundermifflin.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"},{"url":"https://www.nbcstore.com/shop-by-show/the-office.html?shop_by_theme=7","category":"work"},{"url":"http://dundermifflin.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1496708712}
```

## Delete a Company

This request permanently removes a Company from your Copper account.

`DELETE {{base_url}}/companies/{{delete_company_id}}`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

```text

```

### Example Responses

* Delete Person

200: OK

```javascript
{"id":26443553,"is_deleted":true}
```

## List Companies \(Search\)

The /search endpoint provides the ability to list Companies and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned \(the filtering criteria have an 'AND' relationship\).

To see examples of search request using the various parameters, click on the `Companies Search` dropdown on the right. Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Companies, these fields are: city, state, postal\_code, tags, custom dropdown, custom multi-select fields. For an example of how this works, see `Search Companies by Empty Field`. Some fields \(e.g. assignee\_ids\) can also filter for an empty value by specifying -2 as the ID.

To search by custom fields, see `Search Entity by Custom Field` under `Custom Fields` folder.

To change the number of records returned, change the "page\_size" parameter. E.g., specify 200 for a page size of 200 records.

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| page\_number | number | The page number \(starting with 1\) that you would like to view. | 1 |
| page\_size | number | The number of entries included in a page of results | 20 |
| sort\_by | string | The field on which to sort the results \(see footnote 1\). | date\_modified |
| sort\_direction | string | The direction in which to sort the results. Possible values are: asc or desc. | asc |
| name | string | Full name of the Company to search for. | none |
| phone\_number | string | Phone number of the Company to search for. | none |
| email\_domains | string | Email domains of the Company to search for. | none |
| contact\_type\_ids | number\[\] | The contact type Ids to search for \(see footnote 2\). | none |
| assignee\_ids | number\[\] | The ids of Users that Company must be owned by, or -2 for Company with no owner. | none |
| city | string | The city in which Company must be located. | none |
| state | string | The state or province in which Company must be located. | none |
| postal\_code | string | The postal code in which Company must be located. | none |
| country | string | The two character country code where Company must be located. | none |
| tags | string\[\] | Filter Leads to those that match at least one of the tags specified. | none |
| followed | number | 1: followed, 2: not followed | none |
| age | number | The maximum age in seconds that each Company must be. | none |
| minimum\_interaction\_count | number | The minimum number of interactions Company must have had. | none |
| maximum\_interaction\_count | number | The maximum number of interactions Company must have had. | none |
| minimum\_interaction\_date | timestamp | The Unix timestamp of the earliest date of the last interaction. | none |
| maximum\_interaction\_date | timestamp | The Unix timestamp of the latest date of the last interaction. | none |
| minimum\_created\_date | timestamp | The Unix timestamp of the earliest date Company are created. | none |
| maximum\_created\_date | timestamp | The Unix timestamp of the latest date Company are created. | none |

Footnote: 1. Possible fields are: name, phone, contact, contact\_first\_name, contact\_last\_name, date\_modified, date\_created, email\_domain, city, state, country, zip, assignee, contact\_group, last\_interaction, interaction\_count, primary\_website. 2. See `List Contact Types` under Other Resources folder. 3. See `List Opportunities (Search)` under 5. Opportunities folder.

`POST {{base_url}}/companies/search`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

```text
{
  "page_size": 25,
  "sort_by": "name"
}
```

### Example Responses

* Search Companies by Custom Date Field

200: OK

```javascript
[{"id":4,"name":"Sabre Inc (sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":"US"},"assignee_id":2,"contact_type_id":6,"details":null,"email_domain":null,"phone_numbers":[],"socials":[],"tags":["tag1"],"websites":[],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"interaction_count":0,"date_created":1515434867,"date_modified":1516324052}]
```

* Search Companies by Contact Type Ids

200: OK

```javascript
[{"id":4,"name":"Sabre Inc (sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":""},"assignee_id":2,"contact_type_id":6,"details":null,"email_domain":null,"phone_numbers":[],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"interaction_count":0,"date_created":1515434867,"date_modified":1516320789}]
```

* Search Companies by City

200: OK

```javascript
[{"id":4,"name":"Sabre Inc (sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":""},"assignee_id":2,"contact_type_id":6,"details":null,"email_domain":null,"phone_numbers":[],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"interaction_count":0,"date_created":1515434867,"date_modified":1516320789}]
```

* Search Companies by Email Domains

200: OK

```javascript
[
    {
        "id": 2,
        "name": "Dunder Mifflin (sample)",
        "address": {
            "street": "213 West Main Street",
            "city": "Scranton",
            "state": "PA",
            "postal_code": "18501",
            "country": null
        },
        "assignee_id": null,
        "contact_type_id": null,
        "details": null,
        "email_domain": "dundermifflin.com",
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [],
        "tags": [],
        "websites": [
            {
                "url": "http://www.dundermifflin.com/index.shtml",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "interaction_count": 0,
        "date_created": 1519852352,
        "date_modified": 1519852398
    }
]
```

* Companies Search

200: OK

```javascript
[{"id":13358412,"name":"Demo Company","address":{"street":"123 Main St","city":"San Francisco","state":"CA","postal_code":"94105","country":null},"assignee_id":null,"contact_type_id":null,"details":"This is a demo company","email_domain":"democompany.com","phone_numbers":[{"number":"415-123-45678","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://democompany.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1496707930,"date_modified":1496707932},{"id":9607580,"name":"Dunder Mifflin (sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"contact_type_id":null,"details":"This is an update","email_domain":"dundermifflin.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"},{"url":"https://www.nbcstore.com/shop-by-show/the-office.html?shop_by_theme=7","category":"work"},{"url":"http://dundermifflin.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1496708712},{"id":13349319,"name":"Noemail","address":null,"assignee_id":137658,"contact_type_id":451490,"details":null,"email_domain":"noemail.com","phone_numbers":[],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"interaction_count":0,"date_created":1496694264,"date_modified":1496694270},{"id":9607579,"name":"ProsperWorks","address":{"street":"221 Main Street Suite 1350","city":"San Francisco","state":"CA","postal_code":"94105","country":""},"assignee_id":null,"contact_type_id":451493,"details":"Overview: ProsperWorks is the world's first zero input CRM. Designed specifically for Google Apps, ProsperWorks helps companies sell more faster by identifying, organizing and tracking sales opportunities right in Gmail, Calendar and Google Drive. By removing the need for data entry, salespeople can focus on developing business and managers can finally have accurate forecasting with real time activity tracking. ProsperWorks was founded by Jon Lee, Kelly Cheng and Andrew Hu with the commitment to empower small business sales and marketing. Jon was Founder/CEO of three big data companies that solved optimization problems in advertising, gaming and photo sharing. Each company realized successful exits. The team also includes the leaders in engineering and product from Facebook Mobile, BaseCRM and Salesforce. ProsperWorks has raised $10 million in funding from True Ventures, Bloomberg Beta, Crunchfund and other high-profile angel investors. ProsperWorks is based in San Francisco, CA.\n\nApprox. Number of Employees: 30\n\nFounded: 2011\n\nKeywords: Automotive, CRM, Finance, Google, Google Apps, Leadership, Management, Podcasting, SAAS, Sales, Small Business","email_domain":"prosperworks.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[{"url":"https://www.linkedin.com/company/prosperworks-inc-","category":"linkedin"},{"url":"https://twitter.com/ProsperWorks","category":"twitter"},{"url":"https://www.facebook.com/ProsperWorks","category":"facebook"},{"url":"http://klout.com/ProsperWorks","category":"klout"},{"url":"https://angel.co/prosperworks","category":"other"},{"url":"https://plus.google.com/u/0/103594665195397142807","category":"other"},{"url":"http://www.crunchbase.com/organization/prosperworks","category":"other"}],"tags":[],"websites":[{"url":"www.prosperworks.com","category":"work"},{"url":"https://www.prosperworks.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1489018922},{"id":9607581,"name":"Sabre Inc (sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":""},"assignee_id":null,"contact_type_id":null,"details":null,"email_domain":null,"phone_numbers":[],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1489018922}]
```

* Search Companies by Last Interaction

200: OK

```javascript
[{"id":2,"name":"ProsperWorks","address":{"street":"221 Main Street Suite 1350","city":"San Francisco","state":"CA","postal_code":"94105","country":""},"assignee_id":null,"contact_type_id":8,"details":null,"email_domain":"prosperworks.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[{"url":"https://www.linkedin.com/company/prosperworks-inc-","category":"linkedin"}],"tags":[],"websites":[{"url":"www.prosperworks.com","category":"work"},{"url":"https://www.prosperworks.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[9]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"interaction_count":2,"date_created":1515434866,"date_modified":1516324063},{"id":4,"name":"Sabre Inc (sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":"US"},"assignee_id":2,"contact_type_id":6,"details":null,"email_domain":null,"phone_numbers":[],"socials":[],"tags":["tag1"],"websites":[],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"interaction_count":2,"date_created":1515434867,"date_modified":1516324258}]
```

* Search Companies by Postal Code

200: OK

```javascript
[{"id":3,"name":"Dunder Mifflin (sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":"US"},"assignee_id":null,"contact_type_id":5,"details":null,"email_domain":"dundermifflin.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"interaction_count":0,"date_created":1515434866,"date_modified":1516323758}]
```

## See a Company's Activities

This request will show the Activity entries created for a specific Company. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

`POST {{base_url}}/companies/{{example_company_id}}/activities`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

```text
{
  "activity_types": [
    {
      "id": 1,
      "category": "user"
    }
  ]
}
```

### Example Responses

* Company Activities

200: OK

```javascript
[
    {
        "id": 72,
        "parent": {
            "id": 1,
            "type": "company"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Call with Alex",
        "activity_date": 1522695004,
        "old_value": null,
        "new_value": null,
        "date_created": 1522695010,
        "date_modified": 1522695004
    },
    {
        "id": 70,
        "parent": {
            "id": 2,
            "type": "person"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Call with Rob",
        "activity_date": 1522694372,
        "old_value": null,
        "new_value": null,
        "date_created": 1522694392,
        "date_modified": 1522694372
    }
]
```

## List Contact Types

Contact Types are categories into which you can place your People and Companies to classify your relationships with them. The Contact Types API allows you to retrieve the list of Contact Types associated with your Copper account.

| Field | Type | Details |
| :--- | :--- | :--- |
| id | number | Unique identifier for the Contact Type. |
| name | string | The name of the Contact Type. |

`GET {{base_url}}/contact_types`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Example Responses

* Contact Types

200: OK

```javascript
[{"id":451490,"name":"Potential Customer"},{"id":451491,"name":"Current Customer"},{"id":451492,"name":"Uncategorized"},{"id":451493,"name":"Other"}]
```

