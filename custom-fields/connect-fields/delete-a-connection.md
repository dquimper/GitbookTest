## Delete a connection

```DELETE https://api.prosperworks.com/developer_api/v1/related_links/{{connection_id}}```

To delete already existing connections in the connect field, use the delete a connection API.

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Body

```

```
### Example Responses

- Delete a connection

200: OK
```json
{
  "ids": [40085, 40086],
  "is_deleted": true
}
```