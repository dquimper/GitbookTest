## Delete an Opportunity,This request permanently removes a record from your Copper account.
,```DELETE {{base_url}}/opportunities/{{delete_opportunity_id}}```
,### Headers
,Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined,### Body
,```

```,### Example Responses
,- Delete Opportunity
,200: OK,```json
{
  "id": 99999999,
  "is_deleted": true
}
```