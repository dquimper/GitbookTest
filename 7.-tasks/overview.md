# 7. Tasks

A Task is a small unit of work which needs to be completed. The Tasks API allows you to create, view, delete and update your Tasks. You can retrieve individual Tasks, list all Tasks, or use search filters to view subsets of your Tasks.

**Task Properties**

|                   Field                    |    Type     |                                                                     Details                                                                     |
| ------------------------------------------ | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| id                                         | number      | Unique identifier for the Task.                                                                                                                 |
| name*                                      | string      | The name of the Task.                                                                                                                           |
| related_resource                           | identifier  | The primary related resource for the Task.                                                                                                      |
| assignee_id                                | number      | Unique identifier of the User that will be the owner of the Task.                                                                               |
| due_date                                   | number      | The date on which the Task is due.                                                                                                              |
| reminder_date                              | number      | The date on which to receive a reminder about the Task.                                                                                         |
| completed_date                             | number      | The date on which the Task was completed. This is automatically set when the status changes from Open to Completed, and cannot be set directly. |
| priority                                   | string_enum | The priority of the Task. Valid values are: "None", "High".                                                                                     |
| status                                     | string_enum | The status of the Task. Valid values are: "Open", "Completed".                                                                                  |
| details                                    | string      | Description of the Task.                                                                                                                        |
| tags                                       | list        | An array of the tags associated with the Task, represented as strings.                                                                          |
| custom_fields[]                            | list        | An array of custom field values belonging to the Task.                                                                                          |
| custom_fields[].custom_field_definition_id | number      | The id of the Custom Field Definition for which this Custom Field stores a value.                                                               |
| custom_fields[].value                      | mixed       | The value (number, string, option id, or timestamp) of this Custom Field.                                                                       |
| date_created                               | number      | A Unix timestamp representing the time at which this Task was created.                                                                          |
| date_modified                              | number      | A Unix timestamp representing the time at which this Task was last modified.                                                                    |
| \* indicates a required field | | |