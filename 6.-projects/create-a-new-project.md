## Create a New Project

```POST https://api.prosperworks.com/developer_api/v1/projects```

The following fields are required for this request:

"name"

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Body

```
{
  "name":"New Demo Project"
}
```
### Example Responses

- New Project

200: OK
```json
{"id":208105,"name":"New Demo Project","related_resource":null,"assignee_id":null,"status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496713867,"date_modified":1496713867}
```