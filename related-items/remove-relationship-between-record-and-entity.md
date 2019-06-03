## Remove relationship between record and Entity

```DELETE https://api.prosperworks.com/developer_api/v1/{{entity}}/{{entity_id}}/related```

Removing the relationship does not cause any of the records involved to be deleted from the system.

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

- Remove relationship between person and opportunity

200: OK
```json
{"removed":true,"resource":{"id":2827700,"type":"opportunity"}}
```