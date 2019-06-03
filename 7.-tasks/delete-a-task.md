## Delete a Task

```DELETE https://api.prosperworks.com/developer_api/v1/tasks/{{delete_task_id}}```

This request permanently removes a record from your Copper account.

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Body

```

```
### Example Responses

- Delete Task

200: OK
```json
{
  "id": 99999999,
  "is_deleted": true
}
```