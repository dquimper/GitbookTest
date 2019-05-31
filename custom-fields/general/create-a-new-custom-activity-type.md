# Create a New Custom Activity Type

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| name\* | string | Name of the custom activity type. |  |
| icon\_type\* | string | Icon Type. Must be one of: "Message", "Phone", "Event", "Assignment", "Assessment", "Group", "Description", "Speaker Notes", "Forum", "Web", "Loyalty", "Content Paste", "Headset", "Share", "Navigation", "Notification", "Voicemail", "Room", "Edit", "Send", "Videocam", "Play Arrow", "Grocery Store", "Mic", "Camera Mic", "Todo" |  |

\*indicates a required field

`POST {{base_url}}/custom_activity_types`

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
  "name": "New Activity",
  "icon_type": "Phone"
}
```

## Example Responses

* Create a New Custom Activity Type

200: OK

```javascript
{
    "id": 5,
    "company_id": 1,
    "icon_type": "Phone",
    "is_disabled": false,
    "is_interaction": false,
    "name": "New Activity",
    "is_default_task_type": null
}
```

