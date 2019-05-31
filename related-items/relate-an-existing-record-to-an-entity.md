## Relate an existing record to an Entity

```POST {{base_url}}/{{entity}}/{{entity_id}}/related```

Please note that when relating records this way, both records have to exist in the system already.

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

- Relate Opportunity to Person

200: OK
```json
{"added":true,"resource":{"id":2827700,"type":"opportunity"}}
```