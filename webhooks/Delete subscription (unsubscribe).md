## Delete subscription (unsubscribe)
,This is the description of the individual request
,```DELETE {{base_url}}/webhooks/{{example_webhook_id}}```
,### Headers
,Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined,### Body
,```

```,### Example Responses
,- Delete webhook
,200: OK,```json
{"id":17065}
```