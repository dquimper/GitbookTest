## Delete subscription (unsubscribe)

```DELETE https://api.prosperworks.com/developer_api/v1/webhooks/{{example_webhook_id}}```

This is the description of the individual request

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

- Delete webhook

200: OK
```json
{"id":17065}
```