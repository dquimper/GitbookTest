## Fetch a Task by ID

```GET https://api.prosperworks.com/developer_api/v1/tasks/{{example_task_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Get Task

200: OK
```json
{"id":3716920,"name":"My First Task","related_resource":{"id":144296,"type":"project"},"assignee_id":137658,"due_date":1496799000,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496712856,"date_modified":1496712857}
```