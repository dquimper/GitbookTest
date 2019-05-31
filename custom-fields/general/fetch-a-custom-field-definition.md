## Fetch a Custom Field Definition

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