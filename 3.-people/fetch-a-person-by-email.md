## Fetch a Person by Email

```POST {{base_url}}/people/fetch_by_email```

Email address is a unique key for People records in Copper. You can fetch a Person by it's email address using this operation.

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{
  "email": "mycontact_123@noemail.com"
}
```
### Example Responses

- Fetch by Emails

200: OK
```json
{"id":27140442,"name":"My Contact","prefix":null,"first_name":"My","middle_name":null,"last_name":"Contact","suffix":null,"address":null,"assignee_id":null,"company_id":null,"company_name":null,"contact_type_id":451492,"details":null,"emails":[{"email":"mycontact_123@noemail.com","category":"work"}],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"socials":[],"tags":[],"title":null,"websites":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045413,"date_modified":1490045413,"interaction_count":0}
```