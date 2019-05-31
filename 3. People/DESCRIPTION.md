# 3. People

A Person is an individual with whom you communicate. The People API allows you to create, view, delete and update your People. You can retrieve individual People, list all People, or use search filters to view subsets of your People.

**Person Properties**

|            Field            |  Type   |                                      Details                                      |
| --------------------------- | ------- | --------------------------------------------------------------------------------- |
| id                          | number  | Unique identifier for the Person.                                                 |
| name*                        | string  | The first and last name of the Person.                                            |
| address                     | address | An encapsulation of the Person's street, city, state, postal code, and country.   |
| assignee_id                 | number  | Unique identifier of the User that will be the owner of the Person.               |
| company_id                  | string  | The unique identifier of the primary Company with which the Person is associated. |
| company_name                | string  | The name of the primary Company with which the Person is associated.              |
| contact_type_id             | number  | The unique identifier of the Contact Type of the Person.                          |
| details                     | string  | Description of the Person.                                                        |
| emails[]                    | list    | An array of email addresses belonging to the Person.                              |
| emails[].email              | string  | An email address.                                                                 |
| emails[].category           | string  | The category of the email address.                                                |
| phone_numbers[]             | list    | An array of phone numbers belonging to the Person.                                |
| phone_numbers[].number      | string  | A phone number.                                                                   |
| phone_numbers[].category    | string  | The category of the phone number.                                                 |
| socials[]                   | list    | An array of social profiles belonging to the Person.                              |
| socials[].url               | string  | The URL of a social profile.                                                      |
| socials[].category          | string  | The category of the social profile.                                               |
| tags                        | list    | An array of the tags associated with the Person, represented as strings.          |
| title                       | string  | The professional title of the Person.                                             |
| websites[]                  | list    | An array of websites belonging to the Person.                                     |
| websites[].url              | string  | The URL of a website.                                                             |
| websites[].category         | string  | The category of the website.                                                      |
| date_created                | number  | A Unix timestamp representing the time at which this Person was created.          |
| date_modified               | number  | A Unix timestamp representing the time at which this Person was last modified.    |
| custom_fields[]             | list    | An array of custom field values belonging to the Person.                          |
| custom_fields[]             |         |                                                                                   |
| .custom_field_definition_id | number  | The id of the Custom Field Definition for which this Custom Field stores a value. |
| custom_fields[]             |         |                                                                                   |
| .value                      | mixed   | The value (number, string, option id, or timestamp) of this Custom Field.         |
| \* indicates a required field | | |

*Please note that* ***email address is a unique key*** *for People and no two records can have the same email address. If you try to create a new Person with an existing email address, then your request will fail.*

## Fetch a Person by ID
undefined

```GET {{base_url}}/people/{{example_person_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined

## Fetch a Person by Email
Email address is a unique key for People records in Copper. You can fetch a Person by it's email address using this operation.

```POST {{base_url}}/people/fetch_by_email```

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
  "email": "mycontact_123@noemail.com"
}
```
### Example Responses

- Fetch by Emails

200: OK
```json
{"id":27140442,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_123@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045413,"date_modified":1490045413,"interaction_count":0}
```

## Create a New Person
undefined

```POST {{base_url}}/people```

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
  "name":"My Contact",
  "emails": [
    {
    "email":"mycontact_1233@noemail.com",
    "category":"work"
    }
  ],
  "address": {
   	"street": "123 Main Street",
    "city": "Savannah",
    "state": "Georgia",
    "postal_code": "31410", 
    "country": "United States"
  },
  "phone_numbers": [
    {
    "number":"415-123-45678",
    "category":"mobile"
    }
  ]
}
```
### Example Responses

- Create New Person

200: OK
```json
{"id":27140448,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_1233@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045450,"date_modified":1490045450}
```

## Update a Person
Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

The field `company_id` is returned in the JSON response, However, if you would like to unrelate and relate a new `company_id`, use the related items API call to delete and then add a new `company_id` to the person record. For more info, see `Related Items` folder.

```PUT {{base_url}}/people/{{example_person_id}}```

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
  "details":"This is an update"
}
```
### Example Responses

- Person Update

200: OK
```json
{"id":26443553,"name":"Person Default","prefix":null,"first_name":"Person","middle_name":null,"last_name":"Default","suffix":null,"address":{"street":"","city":"","state":"","postal_code":"","country":""},"assignee_id":137658,"company_id":null,"company_name":null,"contact_type_id":451490,"details":"This is an update","emails":[],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018908,"date_modified":1496699863,"interaction_count":0}
```

## Delete a Person
This request permanently removes a Person from your Copper account.

```DELETE {{base_url}}/people/{{example_person_id}}```

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

- Delete Person

200: OK
```json
{"id":26443553,"is_deleted":true}
```

## List People (Search)
The /search endpoint provides the ability to list people and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned (the filtering criteria have an 'AND' relationship).

To see examples of search request using the various parameters, click on the `People Search` dropdown on the right. Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Leads, these fields are: city, state, postal_code, tags, custom dropdown, custom multi-select fields. Some fields (e.g. assignee_ids) can also filter for an empty value by specifying -2 as the ID.

To change the number of records returned, change the "page_size" parameter. E.g., specify 200 for a page size of 200 records.

|           Field           |    Type   |                                    Details                                     | Default    |
| ------------------------- | --------- | ------------------------------------------------------------------------------ | ---------- |
| page_number               | number    | The page number (starting with 1) that you would like to view.                 | 1          |
| page_size                 | number    | The number of entries included in a page of results                            | 20         |
| sort_by                   | string    | The field on which to sort the results (see footnote 1).                       | first_name |
| sort_direction            | string    | The direction in which to sort the results. Possible values are: asc or desc.  | asc        |
| name                      | string    | Full name of the People to search for.                                         | none       |
| phone_number              | string    | Phone number of the People to search for.                                      | none       |
| emails                    | string[]  | Emails of the People to search for.                                            | none       |
| contact_type_ids          | number[]  | The contact type Ids to search for (see footnote 2).                           | none       |
| assignee_ids              | number[]  | The ids of Users that People must be owned by, or -2 for People with no owner. | none       |
| company_ids               | number[]  | The ids of Companies that People belong to, or -2 for People with no company.  | none       |
| opportunity_ids           | number[]  | An array of Opportunity IDs (see footnote 3).                                  | none       |
| city                      | string    | The city in which People must be located.                                      | none       |
| state                     | string    | The state or province in which People must be located.                         | none       |
| postal_code               | string    | The postal code in which People must be located.                               | none       |
| country                   | string    | The two character country code where People must be located.                   | none       |
| tags                      | string[]  | Filter Leads to those that match at least one of the tags specified.           | none       |
| followed                  | number    | 1: followed, 2: not followed                                                   | none       |
| age                       | number    | The maximum age in seconds that People must be.                                | none       |
| minimum_interaction_count | number    | The minimum number of interactions People must have had.                       | none       |
| maximum_interaction_count | number    | The maximum number of interactions People must have had.                       | none       |
| minimum_interaction_date  | timestamp | The Unix timestamp of the earliest date of the last interaction.               | none       |
| maximum_interaction_date  | timestamp | The Unix timestamp of the latest date of the last interaction.                 | none       |
| minimum_created_date      | timestamp | The Unix timestamp of the earliest date People are created.                    | none       |
| maximum_created_date      | timestamp | The Unix timestamp of the latest date People are created.                      | none       |

Footnote:
1. Possible fields are: name, first_name, last_name, title, email, phone, date_modified, date_created, city, state, country, zip.
2. See `List Contact Types` under Other Resources folder.
3. See `List Opportunities (Search)` under 5. Opportunities folder.

```POST {{base_url}}/people/search```

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

- Search People by Custom Multi-Select Dropdown

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [
            "tag1"
        ],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
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
            },
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516312771,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Postal Code

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516311811,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Assignee Id

200: OK
```json
[{"id":4,"name":"Jack James","prefix":null,"first_name":"Jack","middle_name":null,"last_name":"James","suffix":null,"address":{"street":"221 Main Street Suite 1350","city":"San Francisco","state":"CA","postal_code":"94105","country":""},"assignee_id":2,"company_id":2,"company_name":"ProsperWorks","contact_type_id":8,"details":"This is an update","emails":[{"email":"jackjames@prosperworks.com","category":"work"}],"phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[{"url":"www.linkedin.com/pub/jack-james/54/172/b47","category":"linkedin"}],"tags":[],"title":"Customer Support","websites":[{"url":"www.prosperworks.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434863,"date_modified":1516299085,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Custom Multi-Select Dropdown Set to Empty

200: OK
```json
[{"id":4,"name":"Jack James","prefix":null,"first_name":"Jack","middle_name":null,"last_name":"James","suffix":null,"address":{"street":"221 Main Street Suite 1350","city":"San Francisco","state":"CA","postal_code":"94105","country":""},"assignee_id":2,"company_id":2,"company_name":"ProsperWorks","contact_type_id":5,"details":"This is an update","emails":[{"email":"jackjames@prosperworks.com","category":"work"}],"phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[{"url":"www.linkedin.com/pub/jack-james/54/172/b47","category":"linkedin"}],"tags":[],"title":"Customer Support","websites":[{"url":"www.prosperworks.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434863,"date_modified":1516308658,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null},{"id":6,"name":"Jo Bennett, (sample)","prefix":null,"first_name":"Jo","middle_name":null,"last_name":"Bennett","suffix":"(sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":""},"assignee_id":null,"company_id":4,"company_name":"Sabre Inc (sample)","contact_type_id":5,"details":null,"emails":[{"email":"jo@sabreinc.com","category":"work"}],"phone_numbers":[],"socials":[],"tags":[],"title":"CEO","websites":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434865,"date_modified":1515525462,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null},{"id":5,"name":"Michael Scott, (sample)","prefix":null,"first_name":"Michael","middle_name":null,"last_name":"Scott","suffix":"(sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"company_id":3,"company_name":"Dunder Mifflin (sample)","contact_type_id":5,"details":null,"emails":[{"email":"michael@dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"4152225466","category":"work"}],"socials":[],"tags":[],"title":"Regional Manager","websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434864,"date_modified":1516310945,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- List People in Groups of 200

200: OK
```json
[
    {
        "id": 4,
        "name": "Jack James",
        "prefix": null,
        "first_name": "Jack",
        "middle_name": null,
        "last_name": "James",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": 2,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 5,
        "details": "This is an update",
        "emails": [
            {
                "email": "jackjames@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "www.linkedin.com/pub/jack-james/54/172/b47",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Customer Support",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434863,
        "date_modified": 1516308658,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 6,
        "name": "Jo Bennett, (sample)",
        "prefix": null,
        "first_name": "Jo",
        "middle_name": null,
        "last_name": "Bennett",
        "suffix": "(sample)",
        "address": {
            "street": "543 Washington Ave",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "19135",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 4,
        "company_name": "Sabre Inc (sample)",
        "contact_type_id": 5,
        "details": null,
        "emails": [
            {
                "email": "jo@sabreinc.com",
                "category": "work"
            }
        ],
        "phone_numbers": [],
        "socials": [],
        "tags": [],
        "title": "CEO",
        "websites": [],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434865,
        "date_modified": 1515525462,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 3,
        "name": "Jon Lee",
        "prefix": null,
        "first_name": "Jon",
        "middle_name": null,
        "last_name": "Lee",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "jonlee@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/jonlee168",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "CEO",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 12,
                "value": [
                    9
                ]
            },
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434862,
        "date_modified": 1516313029,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 5,
        "name": "Michael Scott, (sample)",
        "prefix": null,
        "first_name": "Michael",
        "middle_name": null,
        "last_name": "Scott",
        "suffix": "(sample)",
        "address": {
            "street": "213 West Main Street",
            "city": "Scranton",
            "state": "PA",
            "postal_code": "18501",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 3,
        "company_name": "Dunder Mifflin (sample)",
        "contact_type_id": 5,
        "details": null,
        "emails": [
            {
                "email": "michael@dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4152225466",
                "category": "work"
            }
        ],
        "socials": [],
        "tags": [],
        "title": "Regional Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com/index.shtml",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434864,
        "date_modified": 1516310945,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [
            "tag1"
        ],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
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
            },
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516313340,
        "date_last_contacted": 1516313330,
        "interaction_count": 2,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Phone Number

200: OK
```json
[
    {
        "id": 4,
        "name": "Jack James",
        "prefix": null,
        "first_name": "Jack",
        "middle_name": null,
        "last_name": "James",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": "This is an update",
        "emails": [
            {
                "email": "jackjames@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "www.linkedin.com/pub/jack-james/54/172/b47",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Customer Support",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434863,
        "date_modified": 1516240218,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 3,
        "name": "Jon Lee",
        "prefix": null,
        "first_name": "Jon",
        "middle_name": null,
        "last_name": "Lee",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "jonlee@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/jonlee168",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "CEO",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434862,
        "date_modified": 1515434877,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Interaction Count

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [
            "tag1"
        ],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
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
            },
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516313340,
        "date_last_contacted": 1516313330,
        "interaction_count": 2,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- People Search

200: OK
```json
[{"id":27140338,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"date_created":1490044880,"date_modified":1490044880,"interaction_count":0},{"id":27140359,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":13349319,"company_name":"Noemail","contact_type_id":451492,"details":null,"emails":[{"email":"mylead@noemail.com","category":"work"}],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"date_created":1490045010,"date_modified":1496694271,"interaction_count":0},{"id":27140372,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mylead_1234@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"date_created":1490045046,"date_modified":1490045046,"interaction_count":0},{"id":27140432,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_1234@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045377,"date_modified":1490045377,"interaction_count":0},{"id":27140442,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_123@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045413,"date_modified":1490045413,"interaction_count":0},{"id":27140448,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_1233@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045450,"date_modified":1490045450,"interaction_count":0},{"id":26443553,"name":"Person Default","prefix":null,"first_name":"Person","middle_name":null,"last_name":"Default","suffix":null,"address":{"street":"","city":"","state":"","postal_code":"","country":""},"assignee_id":137658,"company_id":null,"company_name":null,"contact_type_id":451490,"details":null,"emails":[],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018908,"date_modified":1490115067,"interaction_count":0}]
```
- Search People by State

200: OK
```json
[{"id":6,"name":"Jo Bennett, (sample)","prefix":null,"first_name":"Jo","middle_name":null,"last_name":"Bennett","suffix":"(sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":""},"assignee_id":null,"company_id":4,"company_name":"Sabre Inc (sample)","contact_type_id":5,"details":null,"emails":[{"email":"jo@sabreinc.com","category":"work"}],"phone_numbers":[],"socials":[],"tags":[],"title":"CEO","websites":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434865,"date_modified":1515525462,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null},{"id":5,"name":"Michael Scott, (sample)","prefix":null,"first_name":"Michael","middle_name":null,"last_name":"Scott","suffix":"(sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"company_id":3,"company_name":"Dunder Mifflin (sample)","contact_type_id":5,"details":null,"emails":[{"email":"michael@dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"4152225466","category":"work"}],"socials":[],"tags":[],"title":"Regional Manager","websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434864,"date_modified":1516310945,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Full Name

200: OK
```json
[
    {
        "id": 4,
        "name": "Jack James",
        "prefix": null,
        "first_name": "Jack",
        "middle_name": null,
        "last_name": "James",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": "This is an update",
        "emails": [
            {
                "email": "jackjames@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "www.linkedin.com/pub/jack-james/54/172/b47",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Customer Support",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434863,
        "date_modified": 1516240218,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Followed

200: OK
```json
[{"id":4,"name":"Jack James","prefix":null,"first_name":"Jack","middle_name":null,"last_name":"James","suffix":null,"address":{"street":"221 Main Street Suite 1350","city":"San Francisco","state":"CA","postal_code":"94105","country":""},"assignee_id":2,"company_id":2,"company_name":"ProsperWorks","contact_type_id":5,"details":"This is an update","emails":[{"email":"jackjames@prosperworks.com","category":"work"}],"phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[{"url":"www.linkedin.com/pub/jack-james/54/172/b47","category":"linkedin"}],"tags":[],"title":"Customer Support","websites":[{"url":"www.prosperworks.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434863,"date_modified":1516308658,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Date Added

200: OK
```json
[{"id":7,"name":"Taylor Lowe","prefix":null,"first_name":"Taylor","middle_name":null,"last_name":"Lowe","suffix":null,"address":{"street":"221 Main Street Suite 1350","city":"San Francisco","state":"CA","postal_code":"94105","country":""},"assignee_id":null,"company_id":2,"company_name":"ProsperWorks","contact_type_id":8,"details":null,"emails":[{"email":"taylor@prosperworks.com","category":"work"}],"phone_numbers":[{"number":"4158546956","category":"work"}],"socials":[{"url":"https://www.linkedin.com/in/taylorlowe11","category":"linkedin"}],"tags":[],"title":"Business Development","websites":[{"url":"www.prosperworks.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516262400,"date_modified":1516299712,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Last Interaction Date

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [
            "tag1"
        ],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
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
            },
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516313340,
        "date_last_contacted": 1516313330,
        "interaction_count": 2,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Company Id

200: OK
```json
[
    {
        "id": 4,
        "name": "Jack James",
        "prefix": null,
        "first_name": "Jack",
        "middle_name": null,
        "last_name": "James",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": 2,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": "This is an update",
        "emails": [
            {
                "email": "jackjames@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "www.linkedin.com/pub/jack-james/54/172/b47",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Customer Support",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434863,
        "date_modified": 1516299085,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 3,
        "name": "Jon Lee",
        "prefix": null,
        "first_name": "Jon",
        "middle_name": null,
        "last_name": "Lee",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "jonlee@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/jonlee168",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "CEO",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434862,
        "date_modified": 1515434877,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    },
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516299712,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Custom Date Field

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [
            "tag1"
        ],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516312656,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by Opportunity Ids

200: OK
```json
[{"id":5,"name":"Michael Scott, (sample)","prefix":null,"first_name":"Michael","middle_name":null,"last_name":"Scott","suffix":"(sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"company_id":3,"company_name":"Dunder Mifflin (sample)","contact_type_id":5,"details":null,"emails":[{"email":"michael@dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"4152225466","category":"work"}],"socials":[],"tags":[],"title":"Regional Manager","websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434864,"date_modified":1516310945,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Country

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516311811,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```
- Search People by City

200: OK
```json
[{"id":5,"name":"Michael Scott, (sample)","prefix":null,"first_name":"Michael","middle_name":null,"last_name":"Scott","suffix":"(sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"company_id":3,"company_name":"Dunder Mifflin (sample)","contact_type_id":5,"details":null,"emails":[{"email":"michael@dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"4152225466","category":"work"}],"socials":[],"tags":[],"title":"Regional Manager","websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434864,"date_modified":1516310945,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Contact Type

200: OK
```json
[{"id":6,"name":"Jo Bennett, (sample)","prefix":null,"first_name":"Jo","middle_name":null,"last_name":"Bennett","suffix":"(sample)","address":{"street":"543 Washington Ave","city":"Philadelphia","state":"PA","postal_code":"19135","country":""},"assignee_id":null,"company_id":4,"company_name":"Sabre Inc (sample)","contact_type_id":5,"details":null,"emails":[{"email":"jo@sabreinc.com","category":"work"}],"phone_numbers":[],"socials":[],"tags":[],"title":"CEO","websites":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434865,"date_modified":1515525462,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null},{"id":5,"name":"Michael Scott, (sample)","prefix":null,"first_name":"Michael","middle_name":null,"last_name":"Scott","suffix":"(sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"company_id":3,"company_name":"Dunder Mifflin (sample)","contact_type_id":5,"details":null,"emails":[{"email":"michael@dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"4152225466","category":"work"}],"socials":[],"tags":[],"title":"Regional Manager","websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434864,"date_modified":1515434877,"date_last_contacted":null,"interaction_count":0,"leads_converted_from":[],"date_lead_created":null}]
```
- Search People by Tags

200: OK
```json
[
    {
        "id": 7,
        "name": "Taylor Lowe",
        "prefix": null,
        "first_name": "Taylor",
        "middle_name": null,
        "last_name": "Lowe",
        "suffix": null,
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "Vancouver",
            "state": "BC",
            "postal_code": "A1A1A1",
            "country": "CA"
        },
        "assignee_id": null,
        "company_id": 2,
        "company_name": "ProsperWorks",
        "contact_type_id": 8,
        "details": null,
        "emails": [
            {
                "email": "taylor@prosperworks.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "4158546956",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/in/taylorlowe11",
                "category": "linkedin"
            }
        ],
        "tags": [
            "tag1"
        ],
        "title": "Business Development",
        "websites": [
            {
                "url": "www.prosperworks.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1516262400,
        "date_modified": 1516312015,
        "date_last_contacted": null,
        "interaction_count": 0,
        "leads_converted_from": [],
        "date_lead_created": null
    }
]
```

## See a Person's Activities
This request will show the Activity entries created for a specific Person. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

```POST {{base_url}}/people/{{example_person_id}}/activities```

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

- Person Activities

200: OK
```json
[
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


|Field|Type|Details|
|---|---|---|
|id|number|Unique identifier for the Contact Type.|
|name|string|The name of the Contact Type.|

```GET {{base_url}}/contact_types```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Contact Types

200: OK
```json
[{"id":451490,"name":"Potential Customer"},{"id":451491,"name":"Current Customer"},{"id":451492,"name":"Uncategorized"},{"id":451493,"name":"Other"}]
```