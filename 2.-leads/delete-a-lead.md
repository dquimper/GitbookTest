## Delete a Lead

```DELETE https://api.prosperworks.com/developer_api/v1/leads/{{example_lead_id}}```

This request permanently removes a Lead from your Copper account.

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

- leaddel

200: OK
```json
{"id":8900677,"is_deleted":true}
```