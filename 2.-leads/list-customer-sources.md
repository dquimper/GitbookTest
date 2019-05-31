# List Customer Sources

Customer Sources identify where a particular Lead or Opportunity came from. The Customer Sources API allows you to retrieve the list of Customer Sources associated with your Copper account.

| Field | Details |
| :--- | :--- |
| id \(number\) | Unique\* identifier for the customer source. |
| name \(string\) | Label for the customer source definition |

`GET {{base_url}}/customer_sources`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Customer Sources

200: OK

```javascript
[{"id":331240,"name":"Email"},{"id":331241,"name":"Cold Call"},{"id":331242,"name":"Advertising"}]
```

