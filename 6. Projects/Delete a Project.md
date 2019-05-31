## Delete a Project

This request permanently removes a record from your Copper account.

```DELETE {{base_url}}/projects/{{delete_project_id}}```

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

- Delete Project

200: OK
```json
{
  "id": 99999999,
  "is_deleted": true
}
```