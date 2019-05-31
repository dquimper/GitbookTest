# List All Custom Activity Types

undefined

`GET {{base_url}}/custom_activity_types`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* List All Custom Activity Types

200: OK

```javascript
[
    {
        "id": 1,
        "company_id": 1,
        "icon_type": "Phone",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Phone Call",
        "is_default_task_type": null
    },
    {
        "id": 2,
        "company_id": 1,
        "icon_type": "Event",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Meeting",
        "is_default_task_type": null
    },
    {
        "id": 3,
        "company_id": 1,
        "icon_type": "Todo",
        "is_disabled": false,
        "is_interaction": false,
        "name": "To Do",
        "is_default_task_type": true
    },
    {
        "id": 4,
        "company_id": 1,
        "icon_type": "Event",
        "is_disabled": false,
        "is_interaction": true,
        "name": "Custom Meeting",
        "is_default_task_type": null
    }
]
```

