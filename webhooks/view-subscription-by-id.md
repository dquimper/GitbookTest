## View subscription by ID

```GET https://api.prosperworks.com/developer_api/v1/webhooks{{example_webhook_id}}```

This is the description of the individual request

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- See Webhook by ID

200: OK
```json
{
    "id": 25347,
    "target": "https://your.endpoint.here",
    "type": "person",
    "event": "update",
    "secret": {
        "secret": "hook_source",
        "key": "copper_notifications"
    },
    "created_at": 1496787761
}
```