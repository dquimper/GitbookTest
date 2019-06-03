## Delete a Custom Field Definition

```DELETE https://api.prosperworks.com/developer_api/v1/custom_field_definitions/{{custom_field_definition_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | text
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