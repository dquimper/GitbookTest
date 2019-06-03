## Create new subscription

```POST https://api.prosperworks.com/developer_api/v1/webhooks```

"event" = "new" | "update" | "delete"

"type" = "lead" | "person" | "company" | "opportunity" | "project" | "task"

Also, you may specify an optional hash object called "secret" containing custom key/value pairs that is sent with every notification. Using this secret your notification endpoint can authenticate the request to make sure it is coming from a trusted source.

This example shows the creation of a new notification for events when existing Leads are updated.

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Body

```
{
  "target": "https://your.endpoint.here",
  "type": "lead",
  "event": "update",
  "secret": {
    "secret": "hook_source",
    "key": "copper_notifications"
  }
}
```
### Example Responses

- Create subscription

200: OK
```json
{
    "id": 17065,
    "target": "https://your.endpoint.here",
    "type": "lead",
    "event": "update",
    "secret": {
        "secret": "hook_source",
        "key": "copper_notifications"
    },
    "created_at": 1489173015
}
```