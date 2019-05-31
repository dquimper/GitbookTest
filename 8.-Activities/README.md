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
