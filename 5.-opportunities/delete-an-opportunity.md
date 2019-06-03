## Delete an Opportunity

```DELETE https://api.prosperworks.com/developer_api/v1/opportunities/{{delete_opportunity_id}}```

This request permanently removes a record from your Copper account.

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

- Delete Opportunity

200: OK
```json
{
  "id": 99999999,
  "is_deleted": true
}
```