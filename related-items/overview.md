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