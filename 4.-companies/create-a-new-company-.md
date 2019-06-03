## Create a New Company 

```POST https://api.prosperworks.com/developer_api/v1/companies```

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
  "name":"Demo Company",
  "address": {
   	"street": "123 Main Street",
    "city": "Savannah",
    "state": "Georgia",
    "postal_code": "31410", 
    "country": "United States"
  },
  "email_domain":"democompany.com",
  "details":"This is a demo company",
  "phone_numbers": [
    {
    "number":"415-123-45678",
    "category":"work"
    }
  ]
}
```
### Example Responses

- create company

200: OK
```json
{"id":13358412,"name":"Demo Company","address":{"street":"123 Main St","city":"San Francisco","state":"CA","postal_code":"94105","country":null},"assignee_id":null,"contact_type_id":null,"details":"This is a demo company","email_domain":"democompany.com","phone_numbers":[{"number":"415-123-45678","category":"work"}],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1496707930,"date_modified":1496707930}
```