# List Loss Reasons

Loss Reasons identify why a particular Opportunity was lost. The Loss Reasons API allows you to retrieve the list of Loss Reasons associated with your Copper account.

| Field | Description |
| :--- | :--- |
| id \(number\) | Unique identifier for the Loss Reason. |
| name  \(string\) | The name of the Loss Reason. |

`GET {{base_url}}/loss_reasons`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Loss Reasons

200: OK

```javascript
[{"id":308806,"name":"Price"},{"id":308807,"name":"Features"},{"id":308808,"name":"Competitor"}]
```

