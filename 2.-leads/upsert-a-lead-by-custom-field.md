## UPSERT a Lead (by custom field)

```PUT https://api.prosperworks.com/developer_api/v1/leads/upsert```

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
  "properties": { 
    "name": "My Lead", 
    "email": { 
      "email": "mylead@gmail.test", 
      "category": "work" 
    } 
  }, 
 "match": { 
      "field_name": "custom",
      "field_value": {
      "custom_field_definition_id": 100764,
        "value" : "Some text"    
      }
    }
}
```
### Example Responses

- UPSERT a Leads

200: OK
```json
{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":128735,"value":null}],"date_created":1489531171,"date_modified":1512006056,"date_last_contacted":null}
```