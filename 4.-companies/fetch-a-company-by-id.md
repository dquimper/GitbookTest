# Fetch a Company by ID

undefined

`GET {{base_url}}/companies/{{example_company_id}}`

## Headers

| Key | Value | Description | Type |
| :--- | :--- | :--- | :--- |
| X-PW-AccessToken |  | undefined | undefined |
| X-PW-Application | developer\_api | undefined | undefined |
| X-PW-UserEmail |  | undefined | undefined |
| Content-Type | application/json | undefined | undefined |

## Example Responses

* Company

200: OK

```javascript
{"id":9607580,"name":"Dunder Mifflin (sample)","address":{"street":"213 West Main Street","city":"Scranton","state":"PA","postal_code":"18501","country":""},"assignee_id":null,"contact_type_id":null,"details":"Keywords: Dunder Mifflin, Dunder Mifflin Infinity, Dunder Mifflin Paper, Dunder Mifflin Scranton, Dunder-mifflin, Dunder-mifflin Paper, Dunder-mifflin Scranton, Dundermifflin, NBC, NBC.com, Office 360, Ryan Howard, Scranton Office Supplies, The Office 360, The Office Tv, The Office Tv Series, The Office Tv Show","email_domain":"dundermifflin.com","phone_numbers":[{"number":"4153554776","category":"work"}],"socials":[],"tags":[],"websites":[{"url":"http://www.dundermifflin.com/index.shtml","category":"work"},{"url":"https://www.nbcstore.com/shop-by-show/the-office.html?shop_by_theme=7","category":"work"},{"url":"http://dundermifflin.com","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"interaction_count":0,"date_created":1483988828,"date_modified":1489018922}
```

