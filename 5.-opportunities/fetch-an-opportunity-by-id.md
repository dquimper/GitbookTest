# Fetch an Opportunity by ID

undefined

`GET {{base_url}}/opportunities/{{example_opportunity_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Get Opportunity

200: OK

```javascript
{"id":2827698,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/23/2017","company_id":9607580,"company_name":"Dunder Mifflin (sample)","customer_source_id":331241,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":250000,"win_probability":5,"date_created":1483988829,"date_modified":1489018922,"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}]}
```

