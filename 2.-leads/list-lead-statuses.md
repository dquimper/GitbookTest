# List Lead Statuses

Lead statuses are values that can be assigned to a Lead entity to indicate where they are in the qualification process.

| Field | Description |
| :--- | :--- |
| id \(number\) | Unique identifier for the status |
| name \(string\) | The name of the lead status |
| order \(number\) | The position of the value in the list when displayed in the app |
| is\_default \(boolean\) | Indicates whether this value is selected as default when creating a new record |

`GET {{base_url}}/lead_statuses`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Lead Statuses

200: OK

```javascript
[{"id":208231,"name":"New","order":1,"is_default":true},{"id":208232,"name":"Open","order":2,"is_default":false},{"id":208233,"name":"Unqualified","order":3,"is_default":false},{"id":208234,"name":"Junk","order":4,"is_default":false}]
```

