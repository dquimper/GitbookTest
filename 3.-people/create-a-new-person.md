# Create a New Person

undefined

`POST {{base_url}}/people`

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
  "name":"My Contact",
  "emails": [
    {
    "email":"mycontact_1233@noemail.com",
    "category":"work"
    }
  ],
  "address": {
       "street": "123 Main Street",
    "city": "Savannah",
    "state": "Georgia",
    "postal_code": "31410", 
    "country": "United States"
  },
  "phone_numbers": [
    {
    "number":"415-123-45678",
    "category":"mobile"
    }
  ]
}
```

## Example Responses

* Create New Person

200: OK

```javascript
{"id":27140448,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_1233@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045450,"date_modified":1490045450}
```

