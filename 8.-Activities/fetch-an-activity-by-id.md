## Fetch an Activity by ID

undefined

```GET {{base_url}}/activities/{{example_activity_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Get Activity

200: OK
```json
{"id":3061844454,"parent":{"id":9607580,"type":"company"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"Demo phone call","activity_date":1496710783,"old_value":null,"new_value":null,"date_created":1496710787,"date_modified":1496710783}
```