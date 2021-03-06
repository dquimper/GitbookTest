## Update an existing custom field definition

```PUT https://api.prosperworks.com/developer_api/v1/custom_field_definitions/{{custom_field_definition_id}}```

| Field                 | Type          | Details | Default |
| --------------------- | ------------- | ----------------------- | ---------------------- |
| name*              | string | Name of the Custom Field Definition                     |                      |
| data_type*                  | string | One of the following strings: "Checkbox", "Currency", “Date", "Dropdown", "Float", "MultiSelect", "Percentage", “String", "Text", "URL" |                      |
| available_on              | string array       | List of strings containing one or more of the following: “lead”, “person”, “opportunity”, “company”, "project", "task"                      |                      |
| options          | integer array       | Array of options for Dropdown and MultiSelect fields.  A minimum of one option is required for Dropdown and a minimum of 2 options is required for MultiSelect                      |                      |
| currency            | string | 3-letter country code (e.g., "USD", "CAD")                     |                      |
|\* indicates a required field| | |

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
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