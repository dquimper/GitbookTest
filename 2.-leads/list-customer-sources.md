## List Customer Sources

```GET https://api.prosperworks.com/developer_api/v1/customer_sources```

Customer Sources identify where a particular Lead or Opportunity came from. The Customer Sources API allows you to retrieve the list of Customer Sources associated with your Copper account.

|Field|Details|
|---|---|
|id (number)|Unique* identifier for the customer source.|
|name (string)|  Label for the customer source definition|

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Example Responses

- Customer Sources

200: OK
```json
[{"id":331240,"name":"Email"},{"id":331241,"name":"Cold Call"},{"id":331242,"name":"Advertising"}]
```