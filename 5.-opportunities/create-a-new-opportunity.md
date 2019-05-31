# Create a New Opportunity

The following fields are required for this request:

"name"

"primary\_contact\_id"

`POST {{base_url}}/opportunities`

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
  "name": "New Demo Opportunity",
  "primary_contact_id": 27140359,
  "customer_source_id":331242
}
```

## Example Responses

* New Opportunity

200: OK

```javascript
{"id":4956209,"name":"New Demo Opportunity","assignee_id":null,"close_date":null,"company_id":13349319,"company_name":"Noemail","customer_source_id":331242,"details":null,"loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":27140359,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":null,"win_probability":5,"date_last_contacted":null,"leads_converted_from":[],"date_created":1502158599,"date_modified":1502158599,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]}
```

