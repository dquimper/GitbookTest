# 2. Leads

A Lead is an individual or a company that's interested in your products or services. It's a "catch-all" object that contains information about the contact, the company and the project in one. When Leads are qualified, they are usually converted to a Person, Company and Opportunity.

**Lead Properties**

|                   Field                    |     Type      |                                                     Details                                                     |
| ------------------------------------------ | ------------- | --------------------------------------------------------------------------------------------------------------- |
| id                                         | number        | Unique identifier for the Lead.                                                                                 |
| name*                                       | string        | The first and last name of the Lead.                                                                            |
| address                                    | address       | An encapsulation of the Lead's street, city, state, postal code, and country.                                   |
| assignee_id                                | number        | Unique identifier of the User that will be the owner of the Lead.                                               |
| company_name                               | string        | The name of the company to which the Lead belongs.                                                              |
| customer_source_id                         | number        | Unique identifier of the Customer Source that generated this Lead.                                              |
| details                                    | string        | Description of the Lead.                                                                                        |
| email                                      | email_address | An encapsulation of the Lead's email address and category.                                                      |
| monetary_value                             | number        | The expected monetary value of business with the Lead                                                           |
| phone_numbers[]                            | list          | An array of phone numbers belonging to the Lead.                                                                |
| phone_numbers[].number                     | string        | A phone number.                                                                                                 |
| phone_numbers[].category                   | string        | The category of the phone number.                                                                               |
| socials[]                                  | list          | An array of social profiles belonging to the Lead.                                                              |
| socials[].url                              | string        | The URL of a social profile.                                                                                    |
| socials[].category                         | string        | The category of the social profile.                                                                             |
| status                                     | string_enum   | A string representing the status of the Lead. Valid values are: "New", "Unqualified", "Contacted", "Qualified". |
| tags                                       | list          | An array of the tags associated with the Lead, represented as strings.                                          |
| title                                      | string        | The professional title of the Lead.                                                                             |
| websites[]                                 | list          | An array of websites belonging to the Lead.                                                                     |
| websites[].url                             | string        | The URL of a website.                                                                                           |
| websites[].category                        | string        | The category of the website.                                                                                    |
| custom_fields[]                            | list          | An array of custom field values belonging to the Lead.                                                          |
| custom_fields[].custom_field_definition_id | number        | The id of the Custom Field Definition for which this Custom Field stores a value.                               |
| custom_fields[].value                      | mixed         | The value (number, string, option id, or timestamp) of this Custom Field.                                       |
| date_created                               | number        | A Unix timestamp representing the time at which this Lead was created.                                          |
| date_modified                              | number        | A Unix timestamp representing the time at which this Lead was last modified.                                    |
|\* indicates a required field| | |

## Fetch a Lead by ID
undefined

```GET {{base_url}}/leads/{{example_lead_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Sample Lead

200: OK
```json
{"id":8894157,"name":"Test Lead","prefix":null,"first_name":"Test","last_name":"Lead","middle_name":null,"suffix":null,"address":{"street":"301 Howard St Ste 600","city":"San Francisco","state":"CA","postal_code":"94105","country":"US"},"assignee_id":137658,"company_name":"Lead's Company","customer_source_id":331241,"details":"This is a demo description","email":{"email":"address@workemail.com","category":"work"},"monetary_value":100,"socials":[{"url":"facebook.com/test_lead","category":"facebook"}],"status":"New","status_id":208231,"tags":["tag 1","tag 2"],"title":"Title","websites":[{"url":"www.workwebsite.com","category":"work"}],"phone_numbers":[{"number":"415-999-4321","category":"mobile"},{"number":"415-555-1234","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018784,"date_modified":1489173601}
```

## Create a New Lead
undefined

```POST {{base_url}}/leads```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{
  "name":"My Lead",
  "email": {
    "email":"mylead@noemail.com",
    "category":"work"
  },
  "phone_numbers": [
    {
      "number":"415-123-45678",
      "category":"mobile"
      
    }
  ],
  "address": {
   	"street": "123 Main Street",
    "city": "Savannah",
    "state": "Georgia",
    "postal_code": "31410", 
    "country": "United States"
  },
  "custom_fields": [
    {
      "custom_field_definition_id": 100764,
      "value": "Text fields are 255 chars or less!"
    },
    {
      "custom_field_definition_id": 103481,
      "value": "Text area fields can have long text content"
    }
  ],
  "customer_source_id":331242
}
```
### Example Responses

- Create new Lead

200: OK
```json
{"id":13244480,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":331242,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"},{"custom_field_definition_id":128735,"value":null}],"date_created":1502158444,"date_modified":1502158444,"date_last_contacted":null}
```

## Update a Lead
Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

```PUT {{base_url}}/leads/{{example_lead_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{
  "details": "This is an update"
}
```
### Example Responses

- Update a Lead

200: OK
```json
{"id":8894157,"name":"Test Lead","prefix":null,"first_name":"Test","last_name":"Lead","middle_name":null,"suffix":null,"address":{"street":"301 Howard St Ste 600","city":"San Francisco","state":"CA","postal_code":"94105","country":"US"},"assignee_id":137658,"company_name":"Lead's Company","customer_source_id":331241,"details":"This is an update","email":{"email":"address@workemail.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":100,"socials":[{"url":"facebook.com/test_lead","category":"facebook"}],"status":"New","status_id":208231,"tags":["tag 1","tag 2"],"title":"Title","websites":[{"url":"www.workwebsite.com","category":"work"}],"phone_numbers":[{"number":"415-999-4321","category":"mobile"},{"number":"415-555-1234","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":"A Text Value"},{"custom_field_definition_id":128735,"value":1511942400},{"custom_field_definition_id":184997,"value":[262644,262645]},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018784,"date_modified":1513976942,"date_last_contacted":null}
```

## Delete a Lead
This request permanently removes a Lead from your Copper account.

```DELETE {{base_url}}/leads/{{example_lead_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```

```
### Example Responses

- leaddel

200: OK
```json
{"id":8900677,"is_deleted":true}
```

## UPSERT a Lead
**Functionality**

"Upsert" (update + insert) will atomically do the following:
1. Check for the existence of a Lead matching certain criteria
1. If one exists, update it with the supplied parameters.
1. If not, create a new Lead with the supplied parameters.
1. This is particularly useful to avoid creating duplicate Leads.

**Match Criteria**

The supported match criteria are:
* Name
* Email
* Custom Fields

To match on a Custom Field, the corresponding Custom Field Definition must be available on Leads and included in filters. (These settings may be viewed and edited in the web application via System Settings -> Custom Fields.)

**Match Outcomes**

Match outcomes are handled as follows:

* If no matches are found, create a new Lead.
* If exactly one match is found, update that Lead.
* If more than one match is found, return a 422 response with the IDs of the matching Leads.
* If more than 30 matches are found, return a 422 response without the IDs of the matching Leads.

```PUT {{base_url}}/leads/upsert```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{ 
  "properties": { 
    "name": "My Lead", 
    "email": { 
      "email": "mylead@gmail.test", 
      "category": "work" 
    } 
  }, 
  "match": { 
    "field_name": "email", 
    "field_value": "mylead@gmail.test" 
  } 
}
```
### Example Responses

- UPSERT a Lead

200: OK
```json
{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":128735,"value":null}],"date_created":1489531171,"date_modified":1512006056,"date_last_contacted":null}
```

## UPSERT a Lead (by custom field)
undefined

```PUT {{base_url}}/leads/upsert```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{ 
  "properties": { 
    "name": "My Lead", 
    "email": { 
      "email": "mylead@gmail.test", 
      "category": "work" 
    } 
  }, 
 "match": { 
      "field_name": "custom",
      "field_value": {
      "custom_field_definition_id": 100764,
        "value" : "Some text"    
      }
    }
}
```
### Example Responses

- UPSERT a Leads

200: OK
```json
{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":128735,"value":null}],"date_created":1489531171,"date_modified":1512006056,"date_last_contacted":null}
```

## CONVERT a Lead
This request creates a Person record from a Lead record. Optionally, a Company and an Opportunity record can be created as well in the same process. The Lead record is removed after it has been converted.

| Field       | Type   | Details |
| -----       | ----   | ------- |
| person      | object | Details about the Person to be created by the Lead conversion. Valid fields are name, contact_type_id, and assignee_id.
| company     | object | Details about the Company to which the newly created Person will belong. Valid fields are id or name, and they are mutually exclusive. If a Company id is specified, the new Person will belong to that Company. If the name of an existing Company is specified, the new Person will belong to that Company. If a new name is specified, a new Company will be created with that name, and the new Person will belong to that Company. If you explicitly supply an empty string ("") for the company name, then no Company will be created. By default, fuzzy matching will return a list of candidate companies. An optional Boolean field "exact_match" can be specified if the exact company name is known.
| opportunity | object | Details about the Opportunity to be created by the Lead conversion. Valid fields are name, pipeline_id, pipeline_stage_id, monetary_value, and assignee_id. If unspecified, no Opportunity will be created. If pipeline_stage_id is unspecified, it will default to the first stage in the pipeline. |

```POST {{base_url}}/leads/{{example_leadconvert_id}}/convert```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{
   "details":{
      "person":{
         "name":"John Doe"
      },
      "opportunity":{
         "name":"Demo Project",
         "pipeline_id":213214,
         "pipeline_stage_id":12345,
         "monetary_value":1000
      }
   }
}
```
### Example Responses

- Lead Conversion

200: OK
```json
{"person":{"id":27140359,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":13349319,"company_name":"Noemail","contact_type_id":451492,"details":null,"emails":[{"email":"mylead@noemail.com","category":"work"}],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"date_created":1490045010,"date_modified":1496694264,"interaction_count":0},"company":{"id":13349319,"name":"Noemail","address":null,"assignee_id":137658,"contact_type_id":451490,"details":null,"email_domain":"noemail.com","phone_numbers":[],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"interaction_count":0,"date_created":1496694264,"date_modified":1496694264},"opportunity":{"id":4417020,"name":"Demo Project","assignee_id":null,"close_date":null,"company_id":13349319,"company_name":"Noemail","customer_source_id":null,"details":"","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":27140359,"priority":null,"status":"Open","tags":[],"interaction_count":0,"monetary_value":1000,"win_probability":0,"date_created":1496694264,"date_modified":1496694264,"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}]}}
```

## List Leads (Search)
The /search endpoint provides the ability to list Leads and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned (the filtering criteria have an 'AND' relationship).

To see examples of search request using the various parameters, click on the `Leads Search` dropdown on the right. Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Leads, these fields are: city, state, postal_code, tags, custom dropdown, custom multi-select fields. For an example of how this works, see `Search Leads by Empty Field`. Some fields (e.g. assignee_ids) can also filter for an empty value by specifying -2 as the ID.

To search by custom fields, see `Search Entity by Custom Field` under `Custom Fields` folder.

To change the number of records returned, change the "page_size" parameter. E.g., specify 200 for a page size of 200 records.



|           Field           |    Type   |                                    Details                                    | Default |
| ------------------------- | --------- | ----------------------------------------------------------------------------- | ------- |
| page_number               | number    | The page number (starting with 1) that you would like to view.                | 1       |
| page_size                 | number    | The number of entries included in a page of results                           | 20      |
| sort_by                   | string    | The field on which to sort the results (see footnote 1).                      | name    |
| sort_direction            | string    | The direction in which to sort the results. Possible values are: asc or desc. | asc     |
| name                      | string    | Full name of the Lead to search for.                                          | none    |
| phone_number              | string    | Phone number of the Lead to search for.                                       | none    |
| emails                    | string    | Email of the Lead to search for.                                              | none    |
| assignee_ids              | number[]  | The ids of Users that Leads are assigned to (see footnote 2).                 | none    |
| status_ids                | number[]  | An array of Lead status IDs (see footnote 3).                                 | none    |
| customer_source_ids       | number[]  | An array of customer source IDs (see footnote 4).                             | none    |
| city                      | string    | The city in which Leads must be located.                                      | none    |
| state                     | string    | The state or province in which Leads must be located.                         | none    |
| postal_code               | string    | The postal code in which Leads must be located.                               | none    |
| country                   | string    | The two character country code where Leads must be located.                   | none    |
| tags                      | string[]  | Filter Leads to those that match at least one of the tags specified.          | none    |
| followed                  | number    | 1: followed, 2: not followed                                                  | none    |
| age                       | number    | The maximum age in seconds that each Lead must be.                            | none    |
| minimum_monetary_value    | number    | The minimum monetary value Leads must have.                                   | none    |
| maximum_monetary_value    | number    | The maximum monetary value Leads must have.                                   | none    |
| minimum_interaction_count | number    | The minimum number of interactions Leads must have had.                       | none    |
| maximum_interaction_count | number    | The maximum number of interactions Leads must have had.                       | none    |
| minimum_interaction_date  | timestamp | The Unix timestamp of the earliest date of the last interaction.              | none    |
| maximum_interaction_date  | timestamp | The Unix timestamp of the latest date of the last interaction.                | none    |
| minimum_created_date      | timestamp | The Unix timestamp of the earliest date Leads are created.                    | none    |
| maximum_created_date      | timestamp | The Unix timestamp of the latest date Leads are created.                      | none    |
| minimum_modified_date     | timestamp | The Unix timestamp of the earliest date Leads are modified.                   | none    |
| maximum_modified_date     | timestamp | The Unix timestamp of the latest date Leads are modified.                     | none    |

Foonotes:
1. Possible fields are: name, first_name, last_name, company_name, title, value, email, phone, date_modified, date_created, city, state, country, zip, inactive_days.
   - date_modified and date_created: sorting is from oldest to newest
   - inactive_days: sorting is from newest to oldest
2. To get User IDs, see `List Users` under `Acount and Users` folder. Enter -2 as an ID for no assignee.
3. To get lead status IDs, see `List Lead Statuses` under `Other Resources` folder.
4. To get customer source IDs, see `List Customer Sources` under `Other Resources` folder. Enter -2 as an ID for no customer source.

```POST {{base_url}}/leads/search```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{
  "page_size": 25,
  "sort_by": "name"
}
```
### Example Responses

- Search Leads by Phone Number

200: OK
```json
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 1,
        "monetary_unit": "USD",
        "monetary_value": 2500,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [
            "tag1"
        ],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1515800495,
        "date_last_contacted": 1515796263
    }
]
```
- Search Leads by Empty Field

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2501,"socials":[],"status":"New","status_id":5,"tags":["blah"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1516214189,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":6,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```
- Search Leads by Status Change Date

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```
- Search Leads by Followed

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```
- Search Leads by Custom Date Field

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[]}],"date_created":1515434872,"date_modified":1515800180,"date_last_contacted":1515796263}]
```
- Search Leads by Interaction Count

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```
- Leads Search

200: OK
```json
[{"id":9150547,"name":"My Contact","prefix":null,"first_name":"My","last_name":"Contact","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mycontact@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045162,"date_modified":1490045162},{"id":9150552,"name":"My Contact","prefix":null,"first_name":"My","last_name":"Contact","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":null,"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045237,"date_modified":1490045237},{"id":9150578,"name":"My Contact","prefix":null,"first_name":"My","last_name":"Contact","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":null,"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045279,"date_modified":1490045279},{"id":8982554,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489528899,"date_modified":1489528899},{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489531171,"date_modified":1489531171},{"id":9094361,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489791225,"date_modified":1489791225},{"id":9094364,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"123456789012345678901234567890"},{"custom_field_definition_id":103481,"value":"123456789012345678901234567890"}],"date_created":1489791283,"date_modified":1489791283},{"id":9094371,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------"},{"custom_field_definition_id":103481,"value":"123456789012345678901234567890"}],"date_created":1489791417,"date_modified":1489791417},{"id":9094372,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5-----"},{"custom_field_definition_id":103481,"value":"123456789012345678901234567890"}],"date_created":1489791453,"date_modified":1489791453},{"id":9094373,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5-----"},{"custom_field_definition_id":103481,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------"}],"date_created":1489791470,"date_modified":1489791470},{"id":9094383,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5-----"},{"custom_field_definition_id":103481,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------"}],"date_created":1489791672,"date_modified":1489791672},{"id":9174441,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"text \n text"}],"date_created":1490112942,"date_modified":1490112942},{"id":9174443,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"text /n text"}],"date_created":1490112953,"date_modified":1490112953},{"id":8894157,"name":"Test Lead","prefix":null,"first_name":"Test","last_name":"Lead","middle_name":null,"suffix":null,"address":{"street":"301 Howard St Ste 600","city":"San Francisco","state":"CA","postal_code":"94105","country":"US"},"assignee_id":137658,"company_name":"Lead's Company","customer_source_id":331241,"details":"This is an update","email":{"email":"address@workemail.com","category":"work"},"interaction_count":0,"monetary_value":100,"socials":[{"url":"facebook.com/test_lead","category":"facebook"}],"status":"New","status_id":208231,"tags":["tag 1","tag 2"],"title":"Title","websites":[{"url":"www.workwebsite.com","category":"work"}],"phone_numbers":[{"number":"415-999-4321","category":"mobile"},{"number":"415-555-1234","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018784,"date_modified":1496692911}]
```
- Search Leads by Full Name

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1515800495,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":6,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```
- Search Leads by State

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```
- Search Leads by Tags

200: OK
```json
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 1,
        "monetary_unit": "USD",
        "monetary_value": 2501,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [
            "blah"
        ],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516214189,
        "date_last_contacted": 1515796263
    }
]
```
- Search Leads by Monetary Value

200: OK
```json
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": "USD",
        "monetary_value": 2500,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515795399,
        "date_last_contacted": null
    }
]
```
- Search Leads by Created Date

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```
- Search Leads by Custom Multi-Select Dropdown

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1515800495,"date_last_contacted":1515796263}]
```
- Search Leads by Email

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2501,"socials":[],"status":"New","status_id":5,"tags":["blah"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1516214189,"date_last_contacted":1515796263}]
```
- Search Leads by Postal Code

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```
- Search Leads by Assignee IDs

200: OK
```Text
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 2500,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515783705,
        "date_last_contacted": null
    }
]
```
- Search Leads by Custom Multi-Select Dropdown Set to Empty

200: OK
```json
[{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":6,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```
- Search Leads by Status IDs

200: OK
```json
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 2500,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515783705,
        "date_last_contacted": null
    },
    {
        "id": 5,
        "name": "Pam Beesly (sample)",
        "prefix": null,
        "first_name": "Pam Beesly (sample)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": null,
        "assignee_id": null,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!",
        "email": {
            "email": "pam@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 5000,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [
            "sample"
        ],
        "title": "Office Coordinator",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5105553333",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515525131,
        "date_last_contacted": null
    }
]
```
- List Leads in groups of 200

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2501,"socials":[],"status":"New","status_id":5,"tags":["blah"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434872,"date_modified":1516743967,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null},{"id":12,"name":"Test User","prefix":null,"first_name":"Test","last_name":"User","middle_name":null,"suffix":null,"address":{"street":"123 Abc Rd","city":"San Francisco","state":"CA","postal_code":"94114","country":""},"assignee_id":2,"company_name":null,"customer_source_id":null,"details":null,"email":null,"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":5,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516671366,"date_modified":1516671455,"date_last_contacted":null}]
```
- Search Leads by Country

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```
- Search Leads by City

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```
- Search Leads by Customer Source IDs

200: OK
```json
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 2500,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515786833,
        "date_last_contacted": null
    },
    {
        "id": 5,
        "name": "Pam Beesly (sample)",
        "prefix": null,
        "first_name": "Pam Beesly (sample)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": null,
        "assignee_id": null,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!",
        "email": {
            "email": "pam@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 5000,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [
            "sample"
        ],
        "title": "Office Coordinator",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5105553333",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515525131,
        "date_last_contacted": null
    }
]
```
- Search Leads by Modified Date

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```
- Search Leads by Interaction Date

200: OK
```json
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```

## See a Lead's Activities
This request will show the Activity entries created for a specific Lead. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

```POST {{base_url}}/leads/{{example_lead_id}}/activities```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
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

- Lead Activities

200: OK
```json
[
    {
        "id": 68,
        "parent": {
            "id": 1,
            "type": "lead"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Phone call with Dave",
        "activity_date": 1522455323,
        "old_value": null,
        "new_value": null,
        "date_created": 1522455329,
        "date_modified": 1522455323
    }
]
```

## List Customer Sources
Customer Sources identify where a particular Lead or Opportunity came from. The Customer Sources API allows you to retrieve the list of Customer Sources associated with your Copper account.

|Field|Details|
|---|---|
|id (number)|Unique* identifier for the customer source.|
|name (string)|  Label for the customer source definition|

```GET {{base_url}}/customer_sources```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Customer Sources

200: OK
```json
[{"id":331240,"name":"Email"},{"id":331241,"name":"Cold Call"},{"id":331242,"name":"Advertising"}]
```

## List Lead Statuses
Lead statuses are values that can be assigned to a Lead entity to indicate where they are in the qualification process.

|        Field         |                                  Description                                   |
| -------------------- | ------------------------------------------------------------------------------ |
| id (number)          | Unique identifier for the status                                               |
| name (string)        | The name of the lead status                                                    |
| order (number)       | The position of the value in the list when displayed in the app                |
| is_default (boolean) | Indicates whether this value is selected as default when creating a new record |

```GET {{base_url}}/lead_statuses```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Lead Statuses

200: OK
```json
[{"id":208231,"name":"New","order":1,"is_default":true},{"id":208232,"name":"Open","order":2,"is_default":false},{"id":208233,"name":"Unqualified","order":3,"is_default":false},{"id":208234,"name":"Junk","order":4,"is_default":false}]
```