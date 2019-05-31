# View subscription by ID

This is the description of the individual request

`GET {{base_url}}/webhooks{{example_webhook_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* See Webhook by ID

200: OK

```javascript
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

