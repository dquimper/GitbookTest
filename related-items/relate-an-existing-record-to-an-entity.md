## Relate an existing record to an Entity

```POST https://api.prosperworks.com/developer_api/v1/{{entity}}/{{entity_id}}/related```

Please note that when relating records this way, both records have to exist in the system already.

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
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