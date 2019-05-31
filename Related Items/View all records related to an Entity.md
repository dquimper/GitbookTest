## View all records related to an Entity

undefined

```GET {{base_url}}/{{entity}}/{{entity_id}}/related/```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- All related rcords

200: OK
```json
[{"id":208105,"type":"project"},{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"},{"id":13358412,"type":"company"}]
```