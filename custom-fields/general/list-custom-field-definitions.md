# List Custom Field Definitions

Custom Field Definitions specify account specific fields not included as part of the standard resource fields and allows Copper to be customized to your specific workflow. The Custom Field Definitions API allows you to retrieve the list of Custom Field Definitions associated with your Copper account.

| Field | Type | Details |
| :--- | :--- | :--- |
| id | number | Unique identifier for the custom field definition. |
| name | string | Label for the custom field definition |
| data\_type | string enum | The type of data that should be stored within this custom field. Possible values are: String, Text, Dropdown, Date, Checkbox, Float, URL, Percentage, Currency, Connect |
| currency | string enum | The currency used for this custom field definition. Valid only when the data type is Currency. |
| options | options array | A list of possible dropdown options. Valid only when the data type is Dropdown. |

`GET {{base_url}}/custom_field_definitions`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Custom Field Definitions

200: OK

```javascript
[{"id":100764,"name":"A Text Field","data_type":"String","available_on":["company","opportunity","lead","person"]},{"id":103481,"name":"A Text Area Field","data_type":"Text","available_on":["lead","company","opportunity","person"]},{"id":126240,"name":"Color option","data_type":"Dropdown","available_on":["opportunity","project"],"options":[{"id":167776,"name":"Yellow","rank":4},{"id":167775,"name":"Orange","rank":3},{"id":167774,"name":"Blue","rank":2},{"id":167773,"name":"Green","rank":1},{"id":167772,"name":"Red","rank":0}]}]
```

