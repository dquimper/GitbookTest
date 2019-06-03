## List All Custom Activity Types

```GET https://api.prosperworks.com/developer_api/v1/custom_activity_types```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- List All Custom Activity Types

200: OK
```json
[
    {
        "id": 1,
        "company_id": 1,
        "icon_type": "Phone",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Phone Call",
        "is_default_task_type": null
    },
    {
        "id": 2,
        "company_id": 1,
        "icon_type": "Event",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Meeting",
        "is_default_task_type": null
    },
    {
        "id": 3,
        "company_id": 1,
        "icon_type": "Todo",
        "is_disabled": false,
        "is_interaction": false,
        "name": "To Do",
        "is_default_task_type": true
    },
    {
        "id": 4,
        "company_id": 1,
        "icon_type": "Event",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Custom Meeting",
        "is_default_task_type": null
    }
]
```