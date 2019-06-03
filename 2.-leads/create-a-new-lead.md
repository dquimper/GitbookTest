## Create a New Lead

```POST https://api.prosperworks.com/developer_api/v1/leads```

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
  "name":"My Lead",
  "email": {
    "email":"mylead@noemail.com",
    "category":"work"
  },
  "phone_numbers": [
    {
      "number":"415-123-45678",
      "category":"mobile"
      
    }
  ],
  "address": {
   	"street": "123 Main Street",
    "city": "Savannah",
    "state": "Georgia",
    "postal_code": "31410", 
    "country": "United States"
  },
  "custom_fields": [
    {
      "custom_field_definition_id": 100764,
      "value": "Text fields are 255 chars or less!"
    },
    {
      "custom_field_definition_id": 103481,
      "value": "Text area fields can have long text content"
    }
  ],
  "customer_source_id":331242
}
```
### Example Responses

- Create new Lead

200: OK
```json
{"id":13244480,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":331242,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"},{"custom_field_definition_id":128735,"value":null}],"date_created":1502158444,"date_modified":1502158444,"date_last_contacted":null}
```