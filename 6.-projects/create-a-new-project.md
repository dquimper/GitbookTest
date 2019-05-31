# Create a New Project

The following fields are required for this request:

"name"

`POST {{base_url}}/projects`

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
  "name":"New Demo Project"
}
```

## Example Responses

* New Project

200: OK

```javascript
{"id":208105,"name":"New Demo Project","related_resource":null,"assignee_id":null,"status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496713867,"date_modified":1496713867}
```

