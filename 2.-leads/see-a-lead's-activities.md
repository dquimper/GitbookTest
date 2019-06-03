## See a Lead's Activities

```POST https://api.prosperworks.com/developer_api/v1/leads/{{example_lead_id}}/activities```

This request will show the Activity entries created for a specific Lead. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

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
  "activity_types": [
    {
      "id": 1,
      "category": "user"
    }
  ]
}
```
### Example Responses

- Lead Activities

200: OK
```json
[
    {
        "id": 68,
        "parent": {
            "id": 1,
            "type": "lead"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Phone call with Dave",
        "activity_date": 1522455323,
        "old_value": null,
        "new_value": null,
        "date_created": 1522455329,
        "date_modified": 1522455323
    }
]
```