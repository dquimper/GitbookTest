# View all records related to an Entity

undefined

`GET {{base_url}}/{{entity}}/{{entity_id}}/related/`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* All related rcords

200: OK

```javascript
[{"id":208105,"type":"project"},{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"},{"id":13358412,"type":"company"}]
```

