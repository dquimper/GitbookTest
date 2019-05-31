# Create new subscription

"event" = "new" \| "update" \| "delete"

"type" = "lead" \| "person" \| "company" \| "opportunity" \| "project" \| "task"

Also, you may specify an optional hash object called "secret" containing custom key/value pairs that is sent with every notification. Using this secret your notification endpoint can authenticate the request to make sure it is coming from a trusted source.

This example shows the creation of a new notification for events when existing Leads are updated.

`POST {{base_url}}/webhooks`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Body

```text
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

## Example Responses

* Create subscription

200: OK

```javascript
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

