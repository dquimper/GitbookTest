## Create a New Task

```POST https://api.prosperworks.com/developer_api/v1/tasks```

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
### Example Responses

- Create Task

200: OK
```json
{"id":3726701,"name":"Demo Task","related_resource":{"id":null,"type":null},"assignee_id":137658,"due_date":null,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496771985,"date_modified":1496771985}
```