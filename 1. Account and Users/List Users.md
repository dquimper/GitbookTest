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