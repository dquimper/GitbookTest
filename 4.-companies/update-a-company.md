## Update a Company

```PUT https://api.prosperworks.com/developer_api/v1/companies/{{example_company_id}}```

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

- Update Company

200: OK
```json
{"id":9607580,"name":"Dunder Mifflin (sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"contact_type_id":null,"details":"This is an update","email_domain":"dundermifflin.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"},{"url":"https://www.nbcstore.com/shop-by-show/the-office.html?shop_by_theme=7","category":"work"},{"url":"http://dundermifflin.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1496708712}
```