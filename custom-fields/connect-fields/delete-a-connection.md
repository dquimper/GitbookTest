# Delete a connection

To delete already existing connections in the connect field, use the delete a connection API.

`DELETE {{base_url}}/related_links/{{connection_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Body

```text

```

## Example Responses

* Delete a connection

200: OK

```javascript
{
  "ids": [40085, 40086],
  "is_deleted": true
}
```

