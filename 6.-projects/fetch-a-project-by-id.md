## Fetch a Project by ID

```GET https://api.prosperworks.com/developer_api/v1/projects/{{example_project_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Get project

200: OK
```json
{
    "id": 144296,
    "name": "Customize Your New CRM",
    "related_resource": {
        "id": 9607579,
        "type": "company"
    },
    "assignee_id": null,
    "status": "Open",
    "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
    "tags": [],
    "custom_fields": [],
    "date_created": 1483988830,
    "date_modified": 1496712857
}
```