# Connect Fields

Use connect fields to create custom relationships between records. Common examples include keeping track of the relationship between parent/child companies, people to people referrals, assignments, managers, investors and more. For more use cases, please refer to this [help article](https://support.copper.com/hc/en-us/articles/360001739248-Working-with-Connect-Fields).

## List the connections on specified entity

To retrieve already existing connections in the connect field, use the list the connections API.

`GET {{base_url}}/related_links?custom_field_definition_id={{custom_field_definition_id}}&source_type={{source_type}}&source_id={{source_id}}`

### Parameters

You can include the following parameters in a search request.

| Key | Value | Description |
| :--- | :--- | :--- |
| custom\_field\_definition\_id |  | The Id of the custom field definition. This can be fetched by the custom\_field\_definitions API. |
| source\_type |  | The entity type of the source. Supported sources: "people", "opportunity", "lead", "organization", "project", "user" |
| source\_id |  | The Copper record id for the specified entity type |

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Example Responses

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

## Create a connection

Once you have created connect fields, use the create a connection API to add connections to the connect field.

`POST {{base_url}}/related_links`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

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

### Example Responses

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

## Delete a connection

To delete already existing connections in the connect field, use the delete a connection API.

`DELETE {{base_url}}/related_links/{{connection_id}}`

### Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

### Body

```text

```

### Example Responses

* Delete a connection

200: OK

```javascript
{
  "ids": [40085, 40086],
  "is_deleted": true
}
```

