# Fetch a Project by ID

undefined

`GET {{base_url}}/projects/{{example_project_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Get project

200: OK

```javascript
{
    "id": 144296,
    "name": "Customize Your New CRM",
    "related_resource": {
        "id": 9607579,
        "type": "company"
    },
    "assignee_id": null,
    "status": "Open",
    "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
    "tags": [],
    "custom_fields": [],
    "date_created": 1483988830,
    "date_modified": 1496712857
}
```

