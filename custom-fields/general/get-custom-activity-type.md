## Get Custom Activity Type

```GET https://api.prosperworks.com/developer_api/v1/custom_activity_types/{{custom_activity_type_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Get Custom Activity Type

200: OK
```json
{
    "id": 4,
    "company_id": 1,
    "icon_type": "Event",
    "is_disabled": false,
    "is_interaction": true,
    "name": "Custom Meeting",
    "is_default_task_type": null
}
```