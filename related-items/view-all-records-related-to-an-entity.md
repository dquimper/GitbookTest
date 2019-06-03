## View all records related to an Entity

```GET https://api.prosperworks.com/developer_api/v1/{{entity}}/{{entity_id}}/related/```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- All related rcords

200: OK
```json
[{"id":208105,"type":"project"},{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"},{"id":13358412,"type":"company"}]
```