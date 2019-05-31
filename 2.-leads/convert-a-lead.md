# CONVERT a Lead

This request creates a Person record from a Lead record. Optionally, a Company and an Opportunity record can be created as well in the same process. The Lead record is removed after it has been converted.

| Field | Type | Details |
| :--- | :--- | :--- |
| person | object | Details about the Person to be created by the Lead conversion. Valid fields are name, contact\_type\_id, and assignee\_id. |
| company | object | Details about the Company to which the newly created Person will belong. Valid fields are id or name, and they are mutually exclusive. If a Company id is specified, the new Person will belong to that Company. If the name of an existing Company is specified, the new Person will belong to that Company. If a new name is specified, a new Company will be created with that name, and the new Person will belong to that Company. If you explicitly supply an empty string \(""\) for the company name, then no Company will be created. By default, fuzzy matching will return a list of candidate companies. An optional Boolean field "exact\_match" can be specified if the exact company name is known. |
| opportunity | object | Details about the Opportunity to be created by the Lead conversion. Valid fields are name, pipeline\_id, pipeline\_stage\_id, monetary\_value, and assignee\_id. If unspecified, no Opportunity will be created. If pipeline\_stage\_id is unspecified, it will default to the first stage in the pipeline. |

`POST {{base_url}}/leads/{{example_leadconvert_id}}/convert`

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
   "details":{
      "person":{
         "name":"John Doe"
      },
      "opportunity":{
         "name":"Demo Project",
         "pipeline_id":213214,
         "pipeline_stage_id":12345,
         "monetary_value":1000
      }
   }
}
```

## Example Responses

* Lead Conversion

200: OK

```javascript
{"person":{"id":27140359,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":13349319,"company_name":"Noemail","contact_type_id":451492,"details":null,"emails":[{"email":"mylead@noemail.com","category":"work"}],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"date_created":1490045010,"date_modified":1496694264,"interaction_count":0},"company":{"id":13349319,"name":"Noemail","address":null,"assignee_id":137658,"contact_type_id":451490,"details":null,"email_domain":"noemail.com","phone_numbers":[],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}],"interaction_count":0,"date_created":1496694264,"date_modified":1496694264},"opportunity":{"id":4417020,"name":"Demo Project","assignee_id":null,"close_date":null,"company_id":13349319,"company_name":"Noemail","customer_source_id":null,"details":"","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":27140359,"priority":null,"status":"Open","tags":[],"interaction_count":0,"monetary_value":1000,"win_probability":0,"date_created":1496694264,"date_modified":1496694264,"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"}]}}
```

