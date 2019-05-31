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