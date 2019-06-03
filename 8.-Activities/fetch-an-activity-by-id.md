## Fetch an Activity by ID

```GET https://api.prosperworks.com/developer_api/v1/activities/{{example_activity_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Get Activity

200: OK
```json
{"id":3061844454,"parent":{"id":9607580,"type":"company"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"Demo phone call","activity_date":1496710783,"old_value":null,"new_value":null,"date_created":1496710787,"date_modified":1496710783}
```