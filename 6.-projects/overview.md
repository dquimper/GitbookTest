# 6. Projects

A Project is a large set of work which needs to be completed. The Projects API allows you to create, view, delete and update your Projects. You can retrieve individual Projects, list all Projects, or use search filters to view subsets of your Projects.

**Project Properties**

|                   Field                    |    Type     |                                      Details                                      |
| ------------------------------------------ | ----------- | --------------------------------------------------------------------------------- |
| id                                         | number      | Unique identifier for the Project.                                                |
| name*                                      | string      | The name of the Project.                                                          |
| related_resource                           | identifier  | The primary related resource for the Project.                                     |
| assignee_id                                | number      | Unique identifier of the User that will be the owner of the Project.              |
| status                                     | string_enum | The status of the Project. Valid values are: "Open", "Completed".                 |
| details                                    | string      | Description of the Project.                                                       |
| tags                                       | list        | An array of the tags associated with the Project, represented as strings.         |
| custom_fields[]                            | list        | An array of custom field values belonging to the Project.                         |
| custom_fields[].custom_field_definition_id | number      | The id of the Custom Field Definition for which this Custom Field stores a value. |
| custom_fields[].value                      | mixed       | The value (number, string, option id, or timestamp) of this Custom Field.         |
| date_created                               | number      | A Unix timestamp representing the time at which this Project was created.         |
| date_modified                              | number      | A Unix timestamp representing the time at which this Project was last modified.   |
| \* indicates a required field | | |