## Update an Existing Custom Activity Type

```PUT https://api.prosperworks.com/developer_api/v1/custom_activity_types/{{custom_activity_type_id}}```

|   Field                     | Type   |  Details  |  Default  |
| --------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | - |
| name                        | string | Name of the custom activity type.                                                                                                              |   |
| icon_type                   | string | Icon Type. Must be one of: "Message", "Phone", "Event", "Assignment", "Assessment", "Group", "Description", "Speaker Notes", "Forum", "Web", "Loyalty", "Content Paste", "Headset", "Share", "Navigation", "Notification", "Voicemail", "Room", "Edit", "Send", "Videocam", "Play Arrow", "Grocery Store", "Mic", "Camera Mic", "Todo" | |

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | <your_api_token> |  | 
X-PW-Application | developer_api |  | 
X-PW-UserEmail | <your_email_address> |  | 
Content-Type | application/json |  | 
### Body

```
{
  "icon_type": "Todo"
}

```
### Example Responses

- Update an Existing Custom Activity Type

200: OK
```json
{
    "id": 5,
    "company_id": 1,
    "icon_type": "Todo",
    "is_disabled": false,
    "is_interaction": false,
    "name": "New Activity",
    "is_default_task_type": null
}
```