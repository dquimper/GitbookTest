## Fetch a Lead by ID

```GET https://api.prosperworks.com/developer_api/v1/leads/{{example_lead_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Sample Lead

200: OK
```json
{"id":8894157,"name":"Test Lead","prefix":null,"first_name":"Test","last_name":"Lead","middle_name":null,"suffix":null,"address":{"street":"301 Howard St Ste 600","city":"San Francisco","state":"CA","postal_code":"94105","country":"US"},"assignee_id":137658,"company_name":"Lead's Company","customer_source_id":331241,"details":"This is a demo description","email":{"email":"address@workemail.com","category":"work"},"monetary_value":100,"socials":[{"url":"facebook.com/test_lead","category":"facebook"}],"status":"New","status_id":208231,"tags":["tag 1","tag 2"],"title":"Title","websites":[{"url":"www.workwebsite.com","category":"work"}],"phone_numbers":[{"number":"415-999-4321","category":"mobile"},{"number":"415-555-1234","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018784,"date_modified":1489173601}
```