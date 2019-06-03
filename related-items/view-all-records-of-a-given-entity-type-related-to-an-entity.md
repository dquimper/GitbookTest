## View all records of a given Entity Type related to an Entity

```GET https://api.prosperworks.com/developer_api/v1/{{entity}}/{{entity_id}}/related/{{related_entity_name}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Related Opportunities to Person

200: OK
```json
[{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"}]
```