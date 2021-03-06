## List Contact Types

```GET https://api.prosperworks.com/developer_api/v1/contact_types```

Contact Types are categories into which you can place your People and Companies to classify your relationships with them. The Contact Types API allows you to retrieve the list of Contact Types associated with your Copper account.


|Field|Type|Details|
|---|---|---|
|id|number|Unique identifier for the Contact Type.|
|name|string|The name of the Contact Type.|

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Contact Types

200: OK
```json
[{"id":451490,"name":"Potential Customer"},{"id":451491,"name":"Current Customer"},{"id":451492,"name":"Uncategorized"},{"id":451493,"name":"Other"}]
```