## Fetch Account Details

```GET {{base_url}}/account```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Account Details

200: OK
```json
{"id":100624,"name":"Dev API Sandbox"}
```