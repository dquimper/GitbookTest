## Create a connection,Once you have created connect fields, use the create a connection API to add connections to the connect field.
,```POST {{base_url}}/related_links```
,### Headers
,Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined,### Body
,```
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

```,### Example Responses
,- Create a new connection
,200: OK,```json
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