# Relate an existing record to an Entity

Please note that when relating records this way, both records have to exist in the system already.

`POST {{base_url}}/{{entity}}/{{entity_id}}/related`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Body

```text
{
  "resource": {
    "id": 2827700,
    "type": "opportunity"
  }
}
```

## Example Responses

* Relate Opportunity to Person

200: OK

```javascript
{"added":true,"resource":{"id":2827700,"type":"opportunity"}}
```

