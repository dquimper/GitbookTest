## List Loss Reasons

```GET https://api.prosperworks.com/developer_api/v1/loss_reasons```

Loss Reasons identify why a particular Opportunity was lost. The Loss Reasons API allows you to retrieve the list of Loss Reasons associated with your Copper account.


|     Field     |              Description               |
| ------------- | -------------------------------------- |
| id (number)   | Unique identifier for the Loss Reason. |
| name  (string) | The name of the Loss Reason.          |

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Loss Reasons

200: OK
```json
[{"id":308806,"name":"Price"},{"id":308807,"name":"Features"},{"id":308808,"name":"Competitor"}]
```