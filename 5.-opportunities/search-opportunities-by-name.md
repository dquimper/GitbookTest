# Search Opportunities by Name

This example demonstrates how to search Opportunities by name. The name has to be an exact match for the search to be successful.

`POST {{base_url}}/opportunities/search`

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
  "name":"500 Keyboards (sample)"
}
```

## Example Responses

* Search Opportunities by Name

200: OK

```javascript
[{"id":2827700,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/14/2017","company_id":9607581,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987791,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":50000,"win_probability":10,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1483988829,"date_modified":1496943803,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]}]
```

