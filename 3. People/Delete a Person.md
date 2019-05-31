## Delete a Person

This request permanently removes a Person from your Copper account.

```DELETE {{base_url}}/people/{{example_person_id}}```

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

- Delete Person

200: OK
```json
{"id":26443553,"is_deleted":true}
```