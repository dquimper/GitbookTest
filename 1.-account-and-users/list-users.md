# List Users

**Parameters**

You can include the following parameters in a search request.

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| _Required Parameters_ |  |  |  |
| -- |  |  |  |
| _Optional Parameters_ |  |  |  |
| page\_number | number | The page number \(starting with 1\) that you would like to view. | 1 |
| page\_size | number | The number of entries included in a page of results | 20 |

`POST {{base_url}}/users/search`

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

  "page_number":1,
  "page_size": 200
}
```

## Example Responses

* List of Users

200: OK

```javascript
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

