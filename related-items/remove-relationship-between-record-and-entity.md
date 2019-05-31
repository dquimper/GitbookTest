## Remove relationship between record and Entity

```DELETE {{base_url}}/{{entity}}/{{entity_id}}/related```

Removing the relationship does not cause any of the records involved to be deleted from the system.

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{
  "resource": {
    "id": 2827700,
    "type": "opportunity"
  }
}
```
### Example Responses

- Remove relationship between person and opportunity

200: OK
```json
{"removed":true,"resource":{"id":2827700,"type":"opportunity"}}
```