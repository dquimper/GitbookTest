# 8. Activities

Copper keeps a record of activities for People, Leads, Opportunities, and Companies. The Activities API allows you to view, create, edit, and delete activities.
Activities behave uniquely in that deleted activities can be accessed through the API. However, they will appear only as stubs, identical to the response returned by the delete method, and cannot be modified.

Only "User" type Activities can be created or modified using the developer API. "System" type Activities are read-only.

**Activity Properties**

|     Field     |     Type      |                                       Details                                        |
| ------------- | ------------- | ------------------------------------------------------------------------------------ |
| id            | number        | Unique identifier for the Activity.                                                         |
| type*         | activity_type | The Activity Type of this Activity.                                                         |
| parent*       | identifier    | The Identifier of the resource to which this Activity belongs.                              |
| details*      | string        | When applicable, the text body of this Activity.                                            |
| user_id       | number        | When applicable, the id of the User who performed this Activity.                            |
| activity_date | number        | A Unix timestamp representing the time at which this Activity took place.               |
| old_value     | object        | When applicable, the value of a resource's property before this Activity took place. |
| new_value     | object        | When applicable, the value of a resource's property after this Activity took place.          |
| \* indicates a required field | | |


## Fetch an Activity by ID
undefined

```GET {{base_url}}/activities/{{example_activity_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Get Activity

200: OK
```json
{"id":3061844454,"parent":{"id":9607580,"type":"company"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"Demo phone call","activity_date":1496710783,"old_value":null,"new_value":null,"date_created":1496710787,"date_modified":1496710783}
```

## Create a New Activity
undefined

```POST {{base_url}}/activities```

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
  "parent": {
    "type": "person",
    "id": 27140359
  },
  "type": {
    "category": "user",
    "id": 0
  },
  "details": "This is the description of this note"
  
}
```
### Example Responses

- Create New Note

200: OK
```json
{"id":3064242278,"parent":{"id":27140359,"type":"person"},"type":{"id":0,"category":"user"},"user_id":137658,"details":"This is the description of this note","activity_date":1496772355,"old_value":null,"new_value":null,"date_created":1496772355,"date_modified":1496772355}
```

## Delete an Activity
This request permanently removes a record from your Copper account.

```DELETE {{base_url}}/activities/{{delete_activity_id}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Body

```

```
### Example Responses

- Delete Activity

200: OK
```json
{
  "id": 99999999,
  "is_deleted": true
}
```

## List Activities (Search)
The /search endpoint provides the ability to list records and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned (the filtering criteria have an 'AND' relationship).

To see examples of search request using the various parameters, click on the `Search Activities` dropdown on the right.

|     Field             |      Type       |                               Details                                                                            | Default |
| --------------------- | --------------- | ---------------------------------------------------------------------------------------------------------------- | ------- |
| parent                | hash            | A hash describing the resource to which activities must belong (footnote 1).                                     |         |
| activity_types        | activity_type[] | The activity types to filter results on (footnote 1).                                                            | none    |
| page_number           | number          | The page number (starting with 1) that you would like to view.                                                   | 1       |
| page_size             | number          | The number of entries included in a page of results                                                              | 20      |
| minimum_activity_date | number          | The Unix timestamp of the earliest activity date.                                                                | none    |
| maximum_activity_date | number          | The Unix timestamp of the latest activity date.                                                                  | none    |
| full_result           | boolean         | (Optional) If set to true, search performance improves but duplicate activity logs may be returned (footnote 3). | false   |

Footnotes:
1. Parent is specified by: {"id": parent_id, "type": parent_type}. "parent_type" can be "lead", "person", "company", "opportunity", "project", "task". 
2. Activity types is specified by: {"id": activity_type_id, "category": category }. "activity_type_id" and "category" can be retrieved from `List Activity Types` under `Other Resources` folder.
3. If the List Activities Search endpoint is timing out, a flag `full_result=true` can be added. One can expect to see multiple entries returned for the same activity if an email was sent to multiple users. In order to use this flag, user must have admin capabilities. Otherwise, the flag is ignored.

```POST {{base_url}}/activities/search```

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
  "page_size": 25
}
```
### Example Responses

- Search Activities by Date

200: OK
```json
[{"id":203,"parent":{"id":4,"type":"person"},"type":{"id":1,"category":"system"},"user_id":2,"details":null,"activity_date":1516302332,"old_value":null,"new_value":null,"date_created":1516302332,"date_modified":1516302332}]
```
- Search Activities

200: OK
```json
[{"id":3064242278,"parent":{"id":27140359,"type":"person"},"type":{"id":0,"category":"user"},"user_id":137658,"details":"This is the description of this note","activity_date":1496772355,"old_value":null,"new_value":null,"date_created":1496772355,"date_modified":1496772355},{"id":3061844454,"parent":{"id":9607580,"type":"company"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"This is an update","activity_date":1496710783,"old_value":null,"new_value":null,"date_created":1496710787,"date_modified":1496710783},{"id":3061588719,"parent":{"id":27140442,"type":"person"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"Demo call","activity_date":1496703593,"old_value":null,"new_value":null,"date_created":1496703597,"date_modified":1496703593},{"id":3061845284,"parent":{"id":9607580,"type":"company"},"type":{"id":190712,"category":"user"},"user_id":137658,"details":"Sales discussioin","activity_date":1496327400,"old_value":null,"new_value":null,"date_created":1496710806,"date_modified":1496327400},{"id":2826555341,"parent":{"id":8894157,"type":"lead"},"type":{"id":1,"category":"system"},"user_id":137658,"details":null,"activity_date":1489019921,"old_value":null,"new_value":null,"date_created":1489019921,"date_modified":1489019921},{"id":2826550854,"parent":{"id":8894157,"type":"lead"},"type":{"id":1,"category":"system"},"user_id":137658,"details":null,"activity_date":1489019860,"old_value":null,"new_value":null,"date_created":1489019860,"date_modified":1489019860},{"id":2826550639,"parent":{"id":8894157,"type":"lead"},"type":{"id":1,"category":"system"},"user_id":137658,"details":null,"activity_date":1489019856,"old_value":null,"new_value":null,"date_created":1489019856,"date_modified":1489019856},{"id":2693189358,"parent":{"id":23136297,"type":"person"},"type":{"id":194674,"category":"user"},"user_id":137658,"details":"Talked with assistant, will be back tomorrow","activity_date":1484706603,"old_value":null,"new_value":null,"date_created":1484706614,"date_modified":1484706603},{"id":2693184664,"parent":{"id":23136297,"type":"person"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"Discussed the new product feature","activity_date":1484706298,"old_value":null,"new_value":null,"date_created":1484706292,"date_modified":1484706292},{"id":2677929084,"parent":{"id":23136298,"type":"person"},"type":{"id":190711,"category":"user"},"user_id":137658,"details":"ertyfsxcvplkytet","activity_date":1484096559,"old_value":null,"new_value":null,"date_created":1484096557,"date_modified":1484096557}]
```

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