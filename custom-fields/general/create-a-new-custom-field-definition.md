## Create a new custom field definition

```POST https://api.prosperworks.com/developer_api/v1/custom_field_definitions```

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