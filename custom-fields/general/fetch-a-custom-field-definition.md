## Fetch a Custom Field Definition

```GET https://api.prosperworks.com/developer_api/v1/custom_field_definitions/{{custom_field_definition_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Custom Field Definitioin

200: OK
```json
{"id":126240,"name":"Color option","data_type":"Dropdown","available_on":["opportunity","project"],"options":[{"id":167776,"name":"Yellow","rank":4},{"id":167775,"name":"Orange","rank":3},{"id":167774,"name":"Blue","rank":2},{"id":167773,"name":"Green","rank":1},{"id":167772,"name":"Red","rank":0}]}
```