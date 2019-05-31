# Update a Task

Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

`PUT {{base_url}}/tasks/{{example_task_id}}`

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
  "details":"This is an update"
}
```

## Example Responses

* Update Task

200: OK

```javascript
{"id":3716920,"name":"My First Task","related_resource":{"id":144296,"type":"project"},"assignee_id":137658,"due_date":1496799000,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":"This is an update","tags":[],"custom_fields":[],"date_created":1496712856,"date_modified":1496776369}
```

