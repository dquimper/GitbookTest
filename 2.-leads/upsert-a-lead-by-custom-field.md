# UPSERT a Lead \(by custom field\)

undefined

`PUT {{base_url}}/leads/upsert`

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

## Example Responses

* UPSERT a Leads

200: OK

```javascript
{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":128735,"value":null}],"date_created":1489531171,"date_modified":1512006056,"date_last_contacted":null}
```

