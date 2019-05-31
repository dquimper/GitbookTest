# Related Items

Copper supports relating Leads, People, Companies, Opportunities, Projects and Tasks to each other. In the web and mobile applications, these relationships are typically shown in a "Related Items" sections. The Related Items API allows you to relate resources to each other, to view a resource's related items, and to remove relationships between resources.

All relationships are bidirectional, i.e. relating Resource A to Resource B is functionally equivalent to relating Resource B to Resource A. Relationships can only exist between certain types of entities, and additional restrictions may apply. The following are the allowed relationships between Copper resources:

- Leads: Tasks
- People: Companies (limit 1), Opportunities, Tasks, Projects
- Companies: Opportunities, People, Tasks, Projects
- Opportunities: Companies, People, Tasks, Projects
- Projects: Companies, People, Opportunities, Tasks
- Tasks: Companies, People, Opportunities, Leads, Projects (limit 1 total)

The request URLs for each of these operations are constructed as follows. To find all records related to an entity (e.g. leads), the API endpoint is:

https://api.prosperworks.com/developer_api/v1/leads/{{example_lead_id}}/related

To find all entities (e.g. tasks) related to a particular entity (e.g. leads), the API endpoint is:

https://api.prosperworks.com/developer_api/v1/leads/{{example_lead_id}}/related/tasks

The entities leads and tasks in the above examples can be replaced with any entity types that are related to each other (see above for the complete list).

**Notes**

Related Items may be added or removed, but not modified. (To "modify" a Related Item, remove it and add a new one.)


The Related Items API uses Identifiers (as opposed to full objects) to uniquely identify related items.

## View all records related to an Entity
undefined

```GET {{base_url}}/{{entity}}/{{entity_id}}/related/```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- All related rcords

200: OK
```json
[{"id":208105,"type":"project"},{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"},{"id":13358412,"type":"company"}]
```

## View all records of a given Entity Type related to an Entity
undefined

```GET {{base_url}}/{{entity}}/{{entity_id}}/related/{{related_entity_name}}```

### Headers

Key | Value | Description | Type
--- | --- | --- | ---
X-PW-AccessToken | {{api_token}} | undefined | undefined
X-PW-Application | developer_api | undefined | undefined
X-PW-UserEmail | {{api_email}} | undefined | undefined
Content-Type | application/json | undefined | undefined
### Example Responses

- Related Opportunities to Person

200: OK
```json
[{"id":4417020,"type":"opportunity"},{"id":4418567,"type":"opportunity"}]
```

## Relate an existing record to an Entity
Please note that when relating records this way, both records have to exist in the system already.

```POST {{base_url}}/{{entity}}/{{entity_id}}/related```

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
  "resource": {
    "id": 2827700,
    "type": "opportunity"
  }
}
```
### Example Responses

- Relate Opportunity to Person

200: OK
```json
{"added":true,"resource":{"id":2827700,"type":"opportunity"}}
```

## Remove relationship between record and Entity
Removing the relationship does not cause any of the records involved to be deleted from the system.

```DELETE {{base_url}}/{{entity}}/{{entity_id}}/related```

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
  "resource": {
    "id": 2827700,
    "type": "opportunity"
  }
}
```
### Example Responses

- Remove relationship between person and opportunity

200: OK
```json
{"removed":true,"resource":{"id":2827700,"type":"opportunity"}}
```