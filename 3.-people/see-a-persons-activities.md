## See a Person's Activities

```POST https://api.prosperworks.com/developer_api/v1/people/{{example_person_id}}/activities```

This request will show the Activity entries created for a specific Person. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

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

- Person Activities

200: OK
```json
[
    {
        "id": 70,
        "parent": {
            "id": 2,
            "type": "person"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Call with Rob",
        "activity_date": 1522694372,
        "old_value": null,
        "new_value": null,
        "date_created": 1522694392,
        "date_modified": 1522694372
    }
]
```