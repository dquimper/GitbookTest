## Create a connection

```POST https://api.prosperworks.com/developer_api/v1/related_links```

Once you have created connect fields, use the create a connection API to add connections to the connect field.

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
    "custom_field_definition_id": 169, 
    "source": {
        "id": 1001,
        "entity_type": "lead"
    }, 
    "target": {
    	"id": 1002, 
    "entity_type": "lead"
    }
}

```
### Example Responses

- Create a new connection

200: OK
```json
{
    "id": 2103,
    "custom_field_definition_id": 169,
    "source": {
        "id": 1001,
        "entity_type": "lead",
        "name": "1001"
    },
    "target": {
        "id": 1002,
        "entity_type": "lead",
        "name": "1002"
    }
}
```