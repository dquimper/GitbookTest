# Create a new custom field definition

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| name\* | string | Name of the Custom Field Definition |  |
| data\_type\* | string | One of the following strings: "Checkbox", "Currency", “Date", "Dropdown", "Float", "MultiSelect", "Percentage", “String", "Text", "URL" |  |
| available\_on | string array | List of strings containing one or more of the following: “lead”, “person”, “opportunity”, “company”, "project", "task" |  |
| options | integer array | Array of options for Dropdown and MultiSelect fields.  A minimum of one option is required for Dropdown and a minimum of 2 options is required for MultiSelect |  |
| currency | string | 3-letter country code \(e.g., "USD", "CAD"\) |  |
| \* indicates a required field |  |  |  |

`POST {{base_url}}/custom_field_definitions`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Body

```text
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

## Example Responses

* Create a Currency Custom Field

200: OK

```javascript
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

* Create a Dropdown Custom Field

200: OK

```javascript
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

* Create a String Custom Field

200: OK

```javascript
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

