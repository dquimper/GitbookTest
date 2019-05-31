# Remove relationship between record and Entity

Removing the relationship does not cause any of the records involved to be deleted from the system.

`DELETE {{base_url}}/{{entity}}/{{entity_id}}/related`

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

* Remove relationship between person and opportunity

200: OK

```javascript
{"removed":true,"resource":{"id":2827700,"type":"opportunity"}}
```

