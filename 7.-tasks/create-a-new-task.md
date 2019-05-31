# Create a New Task

undefined

`POST {{base_url}}/tasks`

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
    "name": "Demo task",
    "related_resource": {
        "id": 144296,
        "type": "project"
    },
    "assignee_id": 137658,
    "due_date": 1496799000,
    "reminder_date": null,
    "priority": "None",
    "status": "Open",
    "details": "This needs to be done!",
    "tags": [],
    "custom_fields": []
}
```

## Example Responses

* Create Task

200: OK

```javascript
{"id":3726701,"name":"Demo Task","related_resource":{"id":null,"type":null},"assignee_id":137658,"due_date":null,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496771985,"date_modified":1496771985}
```

