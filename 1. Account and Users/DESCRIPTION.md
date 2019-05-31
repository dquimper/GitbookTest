# 1. Account and Users

Account
=======
An **Account** is created when you sign up with Copper. **Users** that you invite will all be members of this Account. In Copper, customer organizations are called "Companies."

**Account Properties**

| Field |  Type  |              Details               |
| ----- | ------ | ---------------------------------- |
| id    | number | Unique* identifier for the Account |
| name  | string | Name of the account                |

**User Properties**

| Field |  Type  |             Details             |
| ----- | ------ | ------------------------------- |
| id    | number | Unique* identifier for the User |
| name  | string | The User's full name            |
| email | string | The User's email address        |

*A note on ids: Unique identifiers are unique within the scope of a single resource type. For example, a given identifier for a Lead will never be assigned to a different Lead, but a different resource such as a Person could use the same identifier.*


## Fetch Account Details
undefined

```GET {{base_url}}/account```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Account Details

200: OK
```json
{"id":100624,"name":"Dev API Sandbox"}
```

## Fetch User by ID
undefined

```GET {{base_url}}/users/{{example_user_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- User

200: OK
```json
{"id":159258,"name":"Demo User","email":"ehdb@phpbb.uu.gl"}
```

## List Users
**Parameters**

You can include the following parameters in a search request.

|         Field         |  Type  |                            Details                             | Default |
| --------------------- | ------ | -------------------------------------------------------------- | ------- |
| *Required Parameters* |        |                                                                |         |
| --                    |        |                                                                |         |
| *Optional Parameters* |        |                                                                |         |
| page_number           | number | The page number (starting with 1) that you would like to view. | 1       |
| page_size             | number | The number of entries included in a page of results            | 20      |

```POST {{base_url}}/users/search```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```
{

  "page_number":1,
  "page_size": 200
}
```
### Example Responses

- List of Users

200: OK
```json
[
    {
        "id": 137658,
        "name": "John Doe",
        "email": "johndoe@copper.com"
    },
    {
        "id": 159258,
        "name": "Jane Smith",
        "email": "janesmith@copper.com"
    }
]
```