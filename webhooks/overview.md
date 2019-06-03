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
