## Delete a Company

```DELETE https://api.prosperworks.com/developer_api/v1/companies/{{delete_company_id}}```

This request permanently removes a Company from your Copper account.

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

- Delete Person

200: OK
```json
{"id":26443553,"is_deleted":true}
```