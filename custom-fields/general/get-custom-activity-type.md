# Get Custom Activity Type

undefined

`GET {{base_url}}/custom_activity_types/{{custom_activity_type_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Get Custom Activity Type

200: OK

```javascript
{
    "id": 4,
    "company_id": 1,
    "icon_type": "Event",
    "is_disabled": false,
    "is_interaction": true,
    "name": "Custom Meeting",
    "is_default_task_type": null
}
```

