# Create a New Company

undefined

`POST {{base_url}}/companies`

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

## Example Responses

* create company

200: OK

```javascript
{"id":13358412,"name":"Demo Company","address":{"street":"123 Main St","city":"San Francisco","state":"CA","postal_code":"94105","country":null},"assignee_id":null,"contact_type_id":null,"details":"This is a demo company","email_domain":"democompany.com","phone_numbers":[{"number":"415-123-45678","category":"work"}],"socials":[],"tags":[],"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1496707930,"date_modified":1496707930}
```

