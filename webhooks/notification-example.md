# Notification Example

This example shows the notification request your endpoint will receive when a notification is sent. There can be 0 or more secret fields shown, depending on the initial webhook configuration. The "updated\_attributes" field only shows up on an "update" event.

`POST https://your.endpoint.here`

## Body

```text
{
  "ids": [<entity_id_1>, <entity_id_2>, ...],
  "type": "<entity_type>",
  "event": "<event_type>",
  "subscription_id": <subscription_id>,
  "secret_field_1": "<string>",
  "secret_field_2": "<string>",
  "updated_attributes": {
    "field_name": [<old_value>, <new_value>]
  }
}
```

