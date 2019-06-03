## Fetch Account Details

```GET https://api.prosperworks.com/developer_api/v1/account```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Account Details

200: OK
```json
{"id":100624,"name":"Dev API Sandbox"}
```