## List Activity Types

Activity Types identify the types of Activities that occur in Copper. The Activity Types Developer API allows you to retrieve the list of Activity Types associated with your Copper account. There are two categories of Activity Type.


Activity Types with category "user" describe user-entered Activities. By default, Copper has three user-entered activity types: Notes, Phone Calls, and Meetings. Notes have a hard-coded ID of 0. Phone Calls and Meetings are assigned IDs when your Copper account is created. Users may also create Custom Activity Types through the Settings page. These will be assigned IDs when they are created.


Custom Activity Types that have been removed from the list in the Settings page are not deleted from Copper, because they are necessary to correctly handle Activities of those types. These Activity Types are visible through the Developer API for Activity Types, and can be used for filtering Activity searches, but cannot be used to create new Activities.


Activity Types with category "system" describe system-generated Activities. There are currently two system activities: "Property Changed" and "Pipeline Stage Changed". They have hard-coded IDs of 1 and 3 respectively.

|        Field         |  Type   |                                                       Details                                                       |
| -------------------- | ------- | ------------------------------------------------------------------------------------------------------------------- |
| id                   | number  | The id of the Activity Type.                                                                                        |
| category             | string  | The category of the Activity Type. Valid categories: user, system.                                                  |
| name                 | string  | The name of the Activity Type.                                                                                      |
| is_disabled          | boolean | For Custom Activity Types, whether or not the Activity Type is disabled.                                            |
| count_as_interaction | boolean | For Activity Types of category "user", whether or not Activities of this type are counted toward interactions data. |

When supplied as parameters for Activity creation or search, Activity Type objects need only specify the "category" and "id" fields. Any other values provided will be ignored.

```GET {{base_url}}/activity_types```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- List Activity Types

200: OK
```json
{"user":[{"id":0,"category":"user","name":"Note","is_disabled":false,"count_as_interaction":false},{"id":190711,"category":"user","name":"Phone Call","is_disabled":false,"count_as_interaction":true},{"id":190712,"category":"user","name":"Meeting","is_disabled":false,"count_as_interaction":true},{"id":191400,"category":"user","name":"Demo call","is_disabled":false,"count_as_interaction":true},{"id":194674,"category":"user","name":"Call - no connect","is_disabled":false,"count_as_interaction":true}],"system":[{"id":1,"category":"system","name":"Property Changed","is_disabled":false,"count_as_interaction":false},{"id":3,"category":"system","name":"Pipeline Stage Changed","is_disabled":false,"count_as_interaction":false}]}
```