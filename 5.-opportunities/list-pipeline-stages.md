# List Pipeline Stages

Pipeline Stages define the positions of Opportunities within their Pipelines. The Pipeline Stages API allows you to retrieve the list of Pipeline Stages associated with your Copper account.

| Field | Details |
| :--- | :--- |
| id \(number\) | Unique identifier for the Pipeline Stage. |
| name \(string\) | The name of the Pipeline Stage. |
| pipeline\_id \(number\) | The unique identifier of the Pipeline in which this Pipeline Stage is. |
| win\_probability \(number\) | The expected probability of winning an Opportunity in this Pipeline Stage. Valid values are \[0-100\] \(inclusive\). |

`GET {{base_url}}/pipeline_stages`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Pipeline Stages

200: OK

```javascript
[{"id":987790,"name":"Qualified","pipeline_id":213214,"win_probability":5},{"id":987791,"name":"Follow-up","pipeline_id":213214,"win_probability":10},{"id":987792,"name":"Presentation","pipeline_id":213214,"win_probability":20},{"id":987793,"name":"Contract Sent","pipeline_id":213214,"win_probability":40},{"id":987794,"name":"Negotiation","pipeline_id":213214,"win_probability":80},{"id":987795,"name":"First Meeting","pipeline_id":213215,"win_probability":10},{"id":987796,"name":"Partner Meeting","pipeline_id":213215,"win_probability":25},{"id":987797,"name":"Negotiation","pipeline_id":213215,"win_probability":50},{"id":987798,"name":"Term Sheet","pipeline_id":213215,"win_probability":75}]
```

