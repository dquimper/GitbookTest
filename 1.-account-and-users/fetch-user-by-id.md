## Fetch User by ID

```GET {{base_url}}/users/{{example_user_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- User

200: OK
```json
{"id":159258,"name":"Demo User","email":"ehdb@phpbb.uu.gl"}
```