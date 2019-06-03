## Update a Project

```PUT https://api.prosperworks.com/developer_api/v1/projects/{{example_project_id}}```

Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

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
  "details":"This is an update"
}
```
### Example Responses

- Update Project

200: OK
```json
{"id":144296,"name":"Customize Your New CRM","related_resource":{"id":9607579,"type":"company"},"assignee_id":null,"status":"Open","details":"This is an update","tags":[],"custom_fields":[],"date_created":1483988830,"date_modified":1496776314}
```