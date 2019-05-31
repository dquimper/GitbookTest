# Update an Opportunity

Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

`PUT {{base_url}}/opportunities/{{example_opportunity_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Body

```text
{
  "details":"This is an update"
}
```

## Example Responses

* Update Opportunity

200: OK

```javascript
{"id":2827698,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/23/2017","company_id":9607580,"company_name":"Dunder Mifflin (sample)","customer_source_id":331241,"details":"This is an update","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":250000,"win_probability":5,"date_created":1483988829,"date_modified":1496776255,"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}]}
```

