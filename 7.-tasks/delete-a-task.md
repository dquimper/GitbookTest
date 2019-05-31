# Delete a Task

This request permanently removes a record from your Copper account.

`DELETE {{base_url}}/tasks/{{delete_task_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Body

```text

```

## Example Responses

* Delete Task

200: OK

```javascript
{
  "id": 99999999,
  "is_deleted": true
}
```

