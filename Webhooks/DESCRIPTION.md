# Webhooks

Webhooks allow systems integrated with Copper to receive near real-time notification of certain events so that data updates and workflows can be triggered.

Webhook concepts
-----

**Subscription**
Register a URL that notifications will be sent to when a specific event type occurs.

**Event**
A specific action in Copper that triggers a notification.

**Notification**
The object delivered by an https request (webhook) to the specified URL.

Event Types
-----

The following events are available for subscription:
- **Create** = a new record is created
- **Update** = any field in the existing entity record is changed. Excludes: new entity relationships, new Activity or any change in meta data
- **Delete** = an existing record is removed

Events are available for the different entity types as follows.

| Record Type | Create | Update | Delete | type  |
| ----------- | ------ | ------ | ------ | ----- |
| Lead        | yes    | yes    | yes    | "lead"|
| Person      | yes    | yes    | yes    | "person"|
| Company     | yes    | yes    | yes    | "company" |
| Opportunity | yes    | yes    | yes    | "opportunity"|
| Project     | yes    | yes    | yes    | "project"|
| Task        | yes    | yes    | yes    | "task"|
| Activity    | yes    | yes    | yes    | "activity_log"|

Technical considerations
-----
**Subscription count**

You may have up to 100 active subscriptions per account.

**Rate limits**

The number of notifications sent are bound by the following limits:
- 600 notifications per minute per account
- 1,800 notifications per account for every 10 minutes

**Multi-event notifications**

Our notifications always send an array with the IDs of the records involved. The array contains at least 1 ID and may contain up to 30 ID's in a single notification. If more than 30 records are affected then we send multiple notifications, each with up to 30 IDs. Each notification counts as a single request towards the rate limit, regardless of the number of IDs it contains.

**Retries**

Our notifications are fired not more than once per event, and we do not retry them, regardless of the status returned by the notification endpoint.

**HTTPS only**

For security reasons only https:// endpoints are accepted for the notification URL.

Webhook properties
----

|     Field      |    Type    |                           Details                           |
| -------------- | ---------- | ----------------------------------------------------------- |
| id             | Identifier | The unique ID of the subscription                           |
| target         | String     | The URL where the notification will be sent                 |
| type           | String     | The entity type on which the event occurs                   |
| event          | String     | The type of event that triggers the notification "new","update","delete"            |
| secret         | Hash       | (Optional) Hash that stores any information (e.g. for authentication) to pass to the webhook event, in the form { "key1": "value1", "key2": "value2", ... } |
| created_at     | Integer    | The date when the subscription was cretaed                  |


## Create new subscription
"event" = "new" | "update" | "delete"

"type" = "lead" | "person" | "company" | "opportunity" | "project" | "task"

Also, you may specify an optional hash object called "secret" containing custom key/value pairs that is sent with every notification. Using this secret your notification endpoint can authenticate the request to make sure it is coming from a trusted source.

This example shows the creation of a new notification for events when existing Leads are updated.

```POST {{base_url}}/webhooks```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
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

## Delete subscription (unsubscribe)
This is the description of the individual request

```DELETE {{base_url}}/webhooks/{{example_webhook_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```

```
### Example Responses

- Delete webhook

200: OK
```json
{"id":17065}
```

## List all subscriptions
This is the description of the individual request

```GET {{base_url}}/webhooks```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
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

## View subscription by ID
This is the description of the individual request

```GET {{base_url}}/webhooks{{example_webhook_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
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

## Notification Example
This example shows the notification request your endpoint will receive when a notification is sent. There can be 0 or more secret fields shown, depending on the initial webhook configuration. The "updated_attributes" field only shows up on an "update" event.

```POST https://your.endpoint.here```

### Body

```
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