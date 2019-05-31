# See a Company's Activities

This request will show the Activity entries created for a specific Company. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

`POST {{base_url}}/companies/{{example_company_id}}/activities`

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
  "activity_types": [
    {
      "id": 1,
      "category": "user"
    }
  ]
}
```

## Example Responses

* Company Activities

200: OK

```javascript
[
    {
        "id": 72,
        "parent": {
            "id": 1,
            "type": "company"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Call with Alex",
        "activity_date": 1522695004,
        "old_value": null,
        "new_value": null,
        "date_created": 1522695010,
        "date_modified": 1522695004
    },
    {
        "id": 70,
        "parent": {
            "id": 2,
            "type": "person"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Call with Rob",
        "activity_date": 1522694372,
        "old_value": null,
        "new_value": null,
        "date_created": 1522694392,
        "date_modified": 1522694372
    }
]
```

