## Update a Person

```PUT https://api.prosperworks.com/developer_api/v1/people/{{example_person_id}}```

Updates are only applied to fields explicitly specified in the request body. For example, if an update request is made with an empty body, no updates will be made. To remove the value from a field, the request body must specify the target field value as 'null'.

The field `company_id` is returned in the JSON response, However, if you would like to unrelate and relate a new `company_id`, use the related items API call to delete and then add a new `company_id` to the person record. For more info, see `Related Items` folder.

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

- Person Update

200: OK
```json
{"id":26443553,"name":"Person Default","prefix":null,"first_name":"Person","middle_name":null,"last_name":"Default","suffix":null,"address":{"street":"","city":"","state":"","postal_code":"","country":""},"assignee_id":137658,"company_id":null,"company_name":null,"contact_type_id":451490,"details":"This is an update","emails":[],"phone_numbers":[],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018908,"date_modified":1496699863,"interaction_count":0}
```