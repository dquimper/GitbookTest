# List the connections on specified entity

To retrieve already existing connections in the connect field, use the list the connections API.

`GET {{base_url}}/related_links?custom_field_definition_id={{custom_field_definition_id}}&source_type={{source_type}}&source_id={{source_id}}`

## Parameters

You can include the following parameters in a search request.

| Key | Value | Description |
| :--- | :--- | :--- |
| custom\_field\_definition\_id |  | The Id of the custom field definition. This can be fetched by the custom\_field\_definitions API. |
| source\_type |  | The entity type of the source. Supported sources: "people", "opportunity", "lead", "organization", "project", "user" |
| source\_id |  | The Copper record id for the specified entity type |

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* List the connections on specified entity

200: OK

```javascript
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

