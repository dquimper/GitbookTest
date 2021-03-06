## List the connections on specified entity

```GET https://api.prosperworks.com/developer_api/v1/related_links?custom_field_definition_id={{custom_field_definition_id}}&source_type={{source_type}}&source_id={{source_id}}```

To retrieve already existing connections in the connect field, use the list the connections API.

### Parameters

You can include the following parameters in a search request.

Key | Value | Description
--- | --- | ---
custom_field_definition_id | {{custom_field_definition_id}} | The Id of the custom field definition. This can be fetched by the custom_field_definitions API.
source_type | {{source_type}} | The entity type of the source. Supported sources: "people", "opportunity", "lead", "organization", "project", "user"
source_id | {{source_id}} | The Copper record id for the specified entity type
### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- List the connections on specified entity

200: OK
```json
[
    {
        "id": 375,
        "custom_field_definition_id": 172,
        "source": {
            "id": 1021,
            "entity_type": "people",
            "name": "1021"
        },
        "target": {
            "id": 155,
            "entity_type": "user",
            "name": "deque deque"
        }
    }
]
```