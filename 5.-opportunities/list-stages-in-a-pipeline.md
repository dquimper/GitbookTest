# List Stages in a Pipeline

undefined

`GET {{base_url}}/pipeline_stages/pipeline/{pipeline_id}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Stages in a Pipeline

200: OK

```javascript
[{"id":987790,"name":"Qualified","pipeline_id":213214,"win_probability":5},{"id":987791,"name":"Follow-up","pipeline_id":213214,"win_probability":10},{"id":987792,"name":"Presentation","pipeline_id":213214,"win_probability":20},{"id":987793,"name":"Contract Sent","pipeline_id":213214,"win_probability":40},{"id":987794,"name":"Negotiation","pipeline_id":213214,"win_probability":80}]
```

