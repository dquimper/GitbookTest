## Delete a connection

To delete already existing connections in the connect field, use the delete a connection API.

```DELETE {{base_url}}/related_links/{{connection_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
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