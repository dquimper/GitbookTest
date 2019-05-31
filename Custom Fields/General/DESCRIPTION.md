# General

Use custom fields to customize Copper. Custom fields are available on all main objects, Leads, People, Companies, Opportunities, Project and Tasks. To learn more, please visit this [help article](https://support.copper.com/hc/en-us/articles/360000558631-Working-with-Custom-Fields).

## List Custom Field Definitions
Custom Field Definitions specify account specific fields not included as part of the standard resource fields and allows Copper to be customized to your specific workflow. The Custom Field Definitions API allows you to retrieve the list of Custom Field Definitions associated with your Copper account.

|   Field   |     Type      |                                                                            Details                                                                             |
| --------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id        | number        | Unique identifier for the custom field definition.                                                                                                            |
| name      | string        | Label for the custom field definition                                                                                                                          |
| data_type | string enum   | The type of data that should be stored within this custom field. Possible values are: String, Text, Dropdown, Date, Checkbox, Float, URL, Percentage, Currency, Connect |
| currency  | string enum   | The currency used for this custom field definition. Valid only when the data type is Currency.                                                                 |
| options   | options array | A list of possible dropdown options. Valid only when the data type is Dropdown.                                                                                |

```GET {{base_url}}/custom_field_definitions```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Custom Field Definitions

200: OK
```json
[{"id":100764,"name":"A Text Field","data_type":"String","available_on":["company","opportunity","lead","person"]},{"id":103481,"name":"A Text Area Field","data_type":"Text","available_on":["lead","company","opportunity","person"]},{"id":126240,"name":"Color option","data_type":"Dropdown","available_on":["opportunity","project"],"options":[{"id":167776,"name":"Yellow","rank":4},{"id":167775,"name":"Orange","rank":3},{"id":167774,"name":"Blue","rank":2},{"id":167773,"name":"Green","rank":1},{"id":167772,"name":"Red","rank":0}]}]
```

## Create a new custom field definition
| Field                 | Type          | Details | Default |
| --------------------- | ------------- | ----------------------- | ---------------------- |
| name*              | string | Name of the Custom Field Definition                     |                      |
| data_type*                  | string | One of the following strings: "Checkbox", "Currency", “Date", "Dropdown", "Float", "MultiSelect", "Percentage", “String", "Text", "URL" |                      |
| available_on              | string array       | List of strings containing one or more of the following: “lead”, “person”, “opportunity”, “company”, "project", "task"                      |                      |
| options          | integer array       | Array of options for Dropdown and MultiSelect fields.  A minimum of one option is required for Dropdown and a minimum of 2 options is required for MultiSelect                      |                      |
| currency            | string | 3-letter country code (e.g., "USD", "CAD")                     |                      |
|\* indicates a required field| | |

```POST {{base_url}}/custom_field_definitions```

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
  "name": "A Dropdown",
  "data_type": "Dropdown",
  "available_on": [ "lead", "person", "company"],
  "options": [
  	{
  		"name": "Option1"
  	},
  	{
  		"name": "Option2"
  	}
  ]
}
```
### Example Responses

- Create a Currency Custom Field

200: OK
```json
{
    "id": 6,
    "name": "My Currency",
    "canonical_name": null,
    "data_type": "Currency",
    "available_on": [
        "lead",
        "person"
    ],
    "currency": "CAD"
}
```
- Create a Dropdown Custom Field

200: OK
```json
{
    "id": 5,
    "name": "A Dropdown",
    "canonical_name": null,
    "data_type": "Dropdown",
    "available_on": [
        "lead",
        "person",
        "company",
        "project",
        "task"
    ],
    "options": [
        {
            "id": 5,
            "name": "Option1",
            "rank": 0
        },
        {
            "id": 6,
            "name": "Option2",
            "rank": 1
        }
    ]
}
```
- Create a String Custom Field

200: OK
```json
{
    "id": 7,
    "name": "A String",
    "canonical_name": null,
    "data_type": "String",
    "available_on": [
        "lead",
        "person"
    ]
}
```

## Update an existing custom field definition
| Field                 | Type          | Details | Default |
| --------------------- | ------------- | ----------------------- | ---------------------- |
| name*              | string | Name of the Custom Field Definition                     |                      |
| data_type*                  | string | One of the following strings: "Checkbox", "Currency", “Date", "Dropdown", "Float", "MultiSelect", "Percentage", “String", "Text", "URL" |                      |
| available_on              | string array       | List of strings containing one or more of the following: “lead”, “person”, “opportunity”, “company”, "project", "task"                      |                      |
| options          | integer array       | Array of options for Dropdown and MultiSelect fields.  A minimum of one option is required for Dropdown and a minimum of 2 options is required for MultiSelect                      |                      |
| currency            | string | 3-letter country code (e.g., "USD", "CAD")                     |                      |
|\* indicates a required field| | |

```PUT {{base_url}}/custom_field_definitions/{{custom_field_definition_id}}```

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
  "available_on": [ "lead", "person", "opportunity"],
  "options": [
  	{
  		"name": "Option 1"
  	},
  	{
  		"name": "Option 2"
  	},
  	{
  		"name": "Option 3"
  	}
  ]
}
```
### Example Responses

- Update a String Custom Field

200: OK
```json
{
    "id": 7,
    "name": "Renamed String",
    "canonical_name": null,
    "data_type": "String",
    "available_on": []
}
```
- Update options for an existing Dropdown Custom Field

200: OK
```json
{
    "id": 3,
    "name": "A Dropdown",
    "canonical_name": null,
    "data_type": "Dropdown",
    "available_on": [
        "lead",
        "person",
        "opportunity"
    ],
    "options": [
        {
            "id": 7,
            "name": "Option 1",
            "rank": 0
        },
        {
            "id": 8,
            "name": "Option 2",
            "rank": 1
        },
        {
            "id": 9,
            "name": "Option 3",
            "rank": 2
        }
    ]
}
```

## Delete a Custom Field Definition
undefined

```DELETE {{base_url}}/custom_field_definitions/{{custom_field_definition_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | text
### Body

```

```
### Example Responses

- Delete a Custom Field Definition

200: OK
```json
{
    "id": 6,
    "is_deleted": true
}
```

## Fetch a Custom Field Definition
undefined

```GET {{base_url}}/custom_field_definitions/{{custom_field_definition_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Custom Field Definitioin

200: OK
```json
{"id":126240,"name":"Color option","data_type":"Dropdown","available_on":["opportunity","project"],"options":[{"id":167776,"name":"Yellow","rank":4},{"id":167775,"name":"Orange","rank":3},{"id":167774,"name":"Blue","rank":2},{"id":167773,"name":"Green","rank":1},{"id":167772,"name":"Red","rank":0}]}
```

## Search Entity (Leads, People, etc) by Custom Field
Custom fields are available for each of the entities (Leads, People, Companies, Opportunities, Projects, and Tasks). Custom field types include: Text Field, Text Area, Dropdown, Date, Checkbox, Number Field, URL, Percentage, Currency, and Multi-Select Dropdown. Text fields are not searchable at this point. The table below summarizes the behavior of each of these fields.

| Field                 | Type          | Search for Empty Value? | Any, All, None Options |
| --------------------- | ------------- | ----------------------- | ---------------------- |
| Dropdown              | integer array | Yes                     | No                     |
| Date                  | integer range | No                      | No                     |
| Checkbox              | boolean       | No                      | No                     |
| Number Field          | numeric       | No                      | No                     |
| Percentage            | numeric range | No                      | No                     |
| Currency              | integer range | No                      | No                     |
| Multi-Select Dropdown | integer array | Yes                     | Yes                    |

Except for text-related fields, each custom field can be searched via the dev API search endpoint for any of the entities. For Leads, this would be the endpoint `/leads/search`.

Dropdown and Multi-Select Dropdown fields have the additional option of searching for records where dropdown and multi-select dropdown fields are empty. This can be accomplished by adding an additional field: { "allow_empty": true }. Searching by Multi-select dropdown also allows searching if any, all, or none of the dropdown options are to be searched. These options can be used together.

Examples of searching for each of the searchable fields can be found under the dropdown menu on the right. Examples given are for `Leads` and can be easily interchanged with any other entity.

```POST {{base_url}}/{{entity_name_in_plural}}/search```

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

- Search Custom Dropdown Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```
- Search Custom Multi-Select Dropdown Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```
- Search Custom Date Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```
- Search Custom Multi-Select Dropdown Field for Both Set Value and Empty Value

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null},{"id":1,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":5000,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":10,"value":[]},{"custom_field_definition_id":2,"value":null},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":7,"value":null},{"custom_field_definition_id":5,"value":false},{"custom_field_definition_id":3,"value":null}],"date_created":1518656436,"date_modified":1518656436,"date_last_contacted":null}]
```
- Search Custom Dropdown Field for Empty Value

200: OK
```json
[{"id":1,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":5000,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":10,"value":[]},{"custom_field_definition_id":2,"value":null},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":7,"value":null},{"custom_field_definition_id":5,"value":false},{"custom_field_definition_id":3,"value":null}],"date_created":1518656436,"date_modified":1518656436,"date_last_contacted":null}]
```
- Search Custom Currency Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```
- Search Custom Checkbox Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```
- Search Custom Percentage Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```
- Search Custom Number Field

200: OK
```json
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

## List All Custom Activity Types
undefined

```GET {{base_url}}/custom_activity_types```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- List All Custom Activity Types

200: OK
```json
[
    {
        "id": 1,
        "company_id": 1,
        "icon_type": "Phone",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Phone Call",
        "is_default_task_type": null
    },
    {
        "id": 2,
        "company_id": 1,
        "icon_type": "Event",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Meeting",
        "is_default_task_type": null
    },
    {
        "id": 3,
        "company_id": 1,
        "icon_type": "Todo",
        "is_disabled": false,
        "is_interaction": false,
        "name": "To Do",
        "is_default_task_type": true
    },
    {
        "id": 4,
        "company_id": 1,
        "icon_type": "Event",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Custom Meeting",
        "is_default_task_type": null
    }
]
```

## Get Custom Activity Type
undefined

```GET {{base_url}}/custom_activity_types/{{custom_activity_type_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Get Custom Activity Type

200: OK
```json
{
    "id": 4,
    "company_id": 1,
    "icon_type": "Event",
    "is_disabled": false,
    "is_interaction": true,
    "name": "Custom Meeting",
    "is_default_task_type": null
}
```

## Create a New Custom Activity Type
|   Field                     | Type   |  Details  |  Default  |
| --------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | - |
| name*                       | string | Name of the custom activity type.                                                                                                              |   |
| icon_type*                  | string | Icon Type. Must be one of: "Message", "Phone", "Event", "Assignment", "Assessment", "Group", "Description", "Speaker Notes", "Forum", "Web", "Loyalty", "Content Paste", "Headset", "Share", "Navigation", "Notification", "Voicemail", "Room", "Edit", "Send", "Videocam", "Play Arrow", "Grocery Store", "Mic", "Camera Mic", "Todo" | |

*indicates a required field

```POST {{base_url}}/custom_activity_types```

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
  "name": "New Activity",
  "icon_type": "Phone"
}

```
### Example Responses

- Create a New Custom Activity Type

200: OK
```json
{
    "id": 5,
    "company_id": 1,
    "icon_type": "Phone",
    "is_disabled": false,
    "is_interaction": false,
    "name": "New Activity",
    "is_default_task_type": null
}
```

## Update an Existing Custom Activity Type
|   Field                     | Type   |  Details  |  Default  |
| --------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | - |
| name                        | string | Name of the custom activity type.                                                                                                              |   |
| icon_type                   | string | Icon Type. Must be one of: "Message", "Phone", "Event", "Assignment", "Assessment", "Group", "Description", "Speaker Notes", "Forum", "Web", "Loyalty", "Content Paste", "Headset", "Share", "Navigation", "Notification", "Voicemail", "Room", "Edit", "Send", "Videocam", "Play Arrow", "Grocery Store", "Mic", "Camera Mic", "Todo" | |

```PUT {{base_url}}/custom_activity_types/{{custom_activity_type_id}}```

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
  "icon_type": "Todo"
}

```
### Example Responses

- Update an Existing Custom Activity Type

200: OK
```json
{
    "id": 5,
    "company_id": 1,
    "icon_type": "Todo",
    "is_disabled": false,
    "is_interaction": false,
    "name": "New Activity",
    "is_default_task_type": null
}
```