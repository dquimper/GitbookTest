## Fetch User by ID

```GET https://api.prosperworks.com/developer_api/v1/users/{{example_user_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- User

200: OK
```json
{"id":159258,"name":"Demo User","email":"ehdb@phpbb.uu.gl"}
```