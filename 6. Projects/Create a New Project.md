## Create a New Project
,The following fields are required for this request:

"name"
,```POST {{base_url}}/projects```
,### Headers
,Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined,### Body
,```
{
  "name":"New Demo Project"
}
```,### Example Responses
,- New Project
,200: OK,```json
{"id":208105,"name":"New Demo Project","related_resource":null,"assignee_id":null,"status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496713867,"date_modified":1496713867}
```