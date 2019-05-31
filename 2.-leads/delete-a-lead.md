# Delete a Lead

This request permanently removes a Lead from your Copper account.

`DELETE {{base_url}}/leads/{{example_lead_id}}`

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

* leaddel

200: OK

```javascript
{"id":8900677,"is_deleted":true}
```

