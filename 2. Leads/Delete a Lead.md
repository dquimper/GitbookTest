## Delete a Lead
,This request permanently removes a Lead from your Copper account.
,```DELETE {{base_url}}/leads/{{example_lead_id}}```
,### Headers
,Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined,### Body
,```

```,### Example Responses
,- leaddel
,200: OK,```json
{"id":8900677,"is_deleted":true}
```