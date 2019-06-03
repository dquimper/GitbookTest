## Create a New Activity

```POST https://api.prosperworks.com/developer_api/v1/activities```

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
  "parent": {
    "type": "person",
    "id": 27140359
  },
  "type": {
    "category": "user",
    "id": 0
  },
  "details": "This is the description of this note"
  
}
```
### Example Responses

- Create New Note

200: OK
```json
{"id":3064242278,"parent":{"id":27140359,"type":"person"},"type":{"id":0,"category":"user"},"user_id":137658,"details":"This is the description of this note","activity_date":1496772355,"old_value":null,"new_value":null,"date_created":1496772355,"date_modified":1496772355}
```