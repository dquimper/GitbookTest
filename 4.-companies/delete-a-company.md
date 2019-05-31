# Delete a Company

This request permanently removes a Company from your Copper account.

`DELETE {{base_url}}/companies/{{delete_company_id}}`

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

* Delete Person

200: OK

```javascript
{"id":26443553,"is_deleted":true}
```

