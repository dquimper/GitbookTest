## List Pipelines

```GET https://api.prosperworks.com/developer_api/v1/pipelines```

Pipelines define the stages through which Opportunities move as they progress through your sales process. The Pipelines API allows you to retrieve the list of Pipelines associated with your Copper account.


|     Field     |                    Details                    |
| ------------- | --------------------------------------------- |
| id  (number)   | Unique identifier for the Pipeline.           |
| name  (string) | The name of the Pipeline.                     |
| stages  (list) | The list of Pipeline Stages in this Pipelines |

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Pipelines

200: OK
```json
[{"id":213214,"name":"Sales","stages":[{"id":987790,"name":"Qualified","win_probability":5},{"id":987791,"name":"Follow-up","win_probability":10},{"id":987792,"name":"Presentation","win_probability":20},{"id":987793,"name":"Contract Sent","win_probability":40},{"id":987794,"name":"Negotiation","win_probability":80}]},{"id":213215,"name":"Business Development","stages":[{"id":987795,"name":"First Meeting","win_probability":10},{"id":987796,"name":"Partner Meeting","win_probability":25},{"id":987797,"name":"Negotiation","win_probability":50},{"id":987798,"name":"Term Sheet","win_probability":75}]}]
```