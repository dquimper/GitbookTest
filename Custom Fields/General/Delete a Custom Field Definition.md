## Delete a Custom Field Definition,undefined
,```DELETE {{base_url}}/custom_field_definitions/{{custom_field_definition_id}}```
,### Headers
,Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | text,### Body
,```

```,### Example Responses
,- Delete a Custom Field Definition
,200: OK,```json
{
    "id": 6,
    "is_deleted": true
}
```