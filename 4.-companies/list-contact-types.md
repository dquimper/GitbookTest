# List Contact Types

Contact Types are categories into which you can place your People and Companies to classify your relationships with them. The Contact Types API allows you to retrieve the list of Contact Types associated with your Copper account.

| Field | Type | Details |
| :--- | :--- | :--- |
| id | number | Unique identifier for the Contact Type. |
| name | string | The name of the Contact Type. |

`GET {{base_url}}/contact_types`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Contact Types

200: OK

```javascript
[{"id":451490,"name":"Potential Customer"},{"id":451491,"name":"Current Customer"},{"id":451492,"name":"Uncategorized"},{"id":451493,"name":"Other"}]
```

