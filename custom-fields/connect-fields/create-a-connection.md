# Create a connection

Once you have created connect fields, use the create a connection API to add connections to the connect field.

`POST {{base_url}}/related_links`

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

## Example Responses

* Create a new connection

200: OK

```javascript
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

