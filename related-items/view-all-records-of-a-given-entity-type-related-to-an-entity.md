# View all records of a given Entity Type related to an Entity

undefined

`GET {{base_url}}/{{entity}}/{{entity_id}}/related/{{related_entity_name}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Related Opportunities to Person

200: OK

```javascript
[{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"}]
```

