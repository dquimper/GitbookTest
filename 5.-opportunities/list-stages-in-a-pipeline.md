## List Stages in a Pipeline

```GET https://api.prosperworks.com/developer_api/v1/pipeline_stages/pipeline/{pipeline_id}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Stages in a Pipeline

200: OK
```json
[{"id":987790,"name":"Qualified","pipeline_id":213214,"win_probability":5},{"id":987791,"name":"Follow-up","pipeline_id":213214,"win_probability":10},{"id":987792,"name":"Presentation","pipeline_id":213214,"win_probability":20},{"id":987793,"name":"Contract Sent","pipeline_id":213214,"win_probability":40},{"id":987794,"name":"Negotiation","pipeline_id":213214,"win_probability":80}]
```