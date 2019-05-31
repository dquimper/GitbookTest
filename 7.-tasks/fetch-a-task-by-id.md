# Fetch a Task by ID

undefined

`GET {{base_url}}/tasks/{{example_task_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Get Task

200: OK

```javascript
{"id":3716920,"name":"My First Task","related_resource":{"id":144296,"type":"project"},"assignee_id":137658,"due_date":1496799000,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496712856,"date_modified":1496712857}
```

