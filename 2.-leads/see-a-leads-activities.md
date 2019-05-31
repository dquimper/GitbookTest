# See a Lead's Activities

This request will show the Activity entries created for a specific Lead. For more details please see the notes at the [/activities endpoint](https://dev.prosperworks.com).

`POST {{base_url}}/leads/{{example_lead_id}}/activities`

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

* Lead Activities

200: OK

```javascript
[
    {
        "id": 68,
        "parent": {
            "id": 1,
            "type": "lead"
        },
        "type": {
            "id": 1,
            "category": "user"
        },
        "user_id": 1,
        "details": "Phone call with Dave",
        "activity_date": 1522455323,
        "old_value": null,
        "new_value": null,
        "date_created": 1522455329,
        "date_modified": 1522455323
    }
]
```

