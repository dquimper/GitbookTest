# List Tasks \(Search\)

The /search endpoint provides the ability to list people and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned \(the filtering criteria have an 'AND' relationship\).

To see examples of search request using the various parameters, click on the `Tasks Search` dropdown on the right. Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Tasks, these fields are: company, opportunity, city, state, postal\_code, tags, custom dropdown, custom multi-select fields. Some fields \(e.g. assignee\_ids\) can also filter for an empty value by specifying -2 as the ID.

To search by custom fields, see `Search Entity by Custom Field` under `Custom Fields` folder.

To change the number of records returned, change the "page\_size" parameter. E.g., specify 200 for a page size of 200 records.

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| page\_number | number | The page number \(starting with 1\) that you would like to view. | 1 |
| page\_size | number | The number of entries included in a page of results | 20 |
| sort\_by | string | The field on which to sort the results \(see footnote 1\). | due\_date |
| sort\_direction | string | The direction in which to sort the results. Possible values are: asc or desc. | asc |
| assignee\_ids | number\[\] | The ids of Users that Tasks must be owned by, or -2 for Tasks with no owner. | none |
| opportunity\_ids | number\[\] | An array of Opportunity IDs \(see footnote 2\). | none |
| project\_ids | number\[\] | The ids of Projects that Tasks belong to, or -2 for Tasks with no project. | none |
| statuses | string\[\] | Filter Tasks to statuses specified \("Open", "Completed"\). | none |
| tags | string\[\] | Filter Tasks to those that match at least one of the tags specified. | none |
| followed | number | 1: followed, 2: not followed | none |
| minimum\_due\_date | timestamp | The minimum due date Tasks must have. | none |
| maximum\_due\_date | timestamp | The maximum due date Tasks must have. | none |
| minimum\_created\_date | timestamp | The Unix timestamp of the earliest date Tasks are created. | none |
| maximum\_created\_date | timestamp | The Unix timestamp of the latest date Tasks are created. | none |
| minimum\_modified\_date | timestamp | The minimum modified date Tasks must have. | none |
| maximum\_modified\_date | timestamp | The maximum modified date Tasks must have. | none |

Footnote: 1. Possible fields are: name, assigned\_to, related\_to, status, priority, due\_date, reminder\_date, completed\_date, date\_created, date\_modified. 2. See `List Opportunities (Search)` under 5. Opportunities folder.

`POST {{base_url}}/tasks/search`

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
  "page_size": 25,
  "sort_by": "name"
}
```

## Example Responses

* Search Tasks by Assignee Ids

200: OK

```javascript
[{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* Search Tasks by Project Ids

200: OK

```javascript
[{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* Search Tasks by Tags

200: OK

```javascript
[{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* Search Tasks by Multi-Select Dropdown Set to Empty

200: OK

```javascript
[{"id":2,"name":"Follow up on Price Quote (sample)","related_resource":{"id":4,"type":"opportunity"},"assignee_id":null,"due_date":1515517200,"reminder_date":null,"completed_date":1516822940,"priority":"None","status":"Completed","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516822940,"custom_activity_type_id":6}]
```

* Search Tasks by Due Date

200: OK

```javascript
[{"id":3,"name":"Follow up Call (sample)","related_resource":{"id":5,"type":"person"},"assignee_id":null,"due_date":1515776400,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516819079,"custom_activity_type_id":6}]
```

* Search Tasks by Followed

200: OK

```javascript
[{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* Search Tasks by Multi-Select Dropdown

200: OK

```javascript
[{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* Search Tasks by Opportunity Ids

200: OK

```javascript
[{"id":2,"name":"Follow up on Price Quote (sample)","related_resource":{"id":4,"type":"opportunity"},"assignee_id":null,"due_date":1515517200,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516820005,"custom_activity_type_id":6}]
```

* Search Tasks by Statuses

200: OK

```javascript
[{"id":2,"name":"Follow up on Price Quote (sample)","related_resource":{"id":4,"type":"opportunity"},"assignee_id":null,"due_date":1515517200,"reminder_date":null,"completed_date":1516822940,"priority":"None","status":"Completed","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516822940,"custom_activity_type_id":6}]
```

* Search Tasks by Custom Date Field

200: OK

```javascript
[{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* List Tasks in Groups of 200

200: OK

```javascript
[{"id":1,"name":"Download ProsperWorks Mobile App","related_resource":{"id":2,"type":"company"},"assignee_id":null,"due_date":1516813200,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":"Visit the Google Play store or the Apple App store to download the ProsperWorks Android or iPhone app.","tags":[],"custom_fields":[{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":12,"value":[9]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516824438,"custom_activity_type_id":6},{"id":3,"name":"Follow up Call (sample)","related_resource":{"id":5,"type":"person"},"assignee_id":null,"due_date":1515776400,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":12,"value":[9]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516824426,"custom_activity_type_id":6},{"id":2,"name":"Follow up on Price Quote (sample)","related_resource":{"id":4,"type":"opportunity"},"assignee_id":null,"due_date":1515517200,"reminder_date":null,"completed_date":1516822940,"priority":"None","status":"Completed","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434871,"date_modified":1516822940,"custom_activity_type_id":6},{"id":6,"name":"New CRM Task","related_resource":{"id":1,"type":"project"},"assignee_id":2,"due_date":1516905000,"reminder_date":null,"completed_date":null,"priority":"High","status":"Open","details":null,"tags":["tag1"],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516818999,"date_modified":1516819000,"custom_activity_type_id":6}]
```

* Tasks Search

200: OK

```javascript
[{"id":3726701,"name":"Demo Task","related_resource":{"id":null,"type":null},"assignee_id":137658,"due_date":null,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1496771985,"date_modified":1496771985},{"id":2277769,"name":"Download ProsperWorks Mobile App","related_resource":{"id":9607579,"type":"company"},"assignee_id":null,"due_date":null,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":"Visit the Google Play store or the Apple App store to download the ProsperWorks Android or iPhone app.","tags":[],"custom_fields":[],"date_created":1483988829,"date_modified":1483989349},{"id":2277771,"name":"Follow up Call (sample)","related_resource":{"id":null,"type":null},"assignee_id":null,"due_date":1483894800,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1483988829,"date_modified":1489018922},{"id":2277770,"name":"Follow up on Price Quote (sample)","related_resource":{"id":null,"type":null},"assignee_id":null,"due_date":1484067600,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":null,"tags":[],"custom_fields":[],"date_created":1483988829,"date_modified":1483988829},{"id":3716920,"name":"My First Task","related_resource":{"id":144296,"type":"project"},"assignee_id":137658,"due_date":1496799000,"reminder_date":null,"completed_date":null,"priority":"None","status":"Open","details":"This is an update","tags":[],"custom_fields":[],"date_created":1496712856,"date_modified":1496776369}]
```

