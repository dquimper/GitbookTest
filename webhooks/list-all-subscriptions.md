## List all subscriptions

```GET https://api.prosperworks.com/developer_api/v1/webhooks```

This is the description of the individual request

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- List all subscriptions

200: OK
```json
[
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
    },
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
    },
    {
        "id": 39285,
        "target": "https://hookb.in/KAnAXW5q",
        "type": "activity_log",
        "event": "update",
        "secret": {
            "secret": "hook_source",
            "key": "copper_notifications"
        },
        "created_at": 1510271719
    },
    {
        "id": 39286,
        "target": "https://hookb.in/KAnAXW5q",
        "type": "activity_log",
        "event": "delete",
        "secret": {
            "secret": "hook_source",
            "key": "copper_notifications"
        },
        "created_at": 1510271965
    },
    {
        "id": 39287,
        "target": "https://hookbin.com/bin/KAnAXW5q",
        "type": "lead",
        "event": "new",
        "secret": {
            "secret": "hook_source",
            "key": "copper_notifications"
        },
        "created_at": 1510272356
    },
    {
        "id": 39288,
        "target": "https://hookbin.com/bin/KAnAXW5q",
        "type": "activity_log",
        "event": "new",
        "secret": {
            "secret": "hook_source",
            "key": "copper_notifications"
        },
        "created_at": 1510272369
    }
]
```