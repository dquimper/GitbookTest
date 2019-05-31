# UPSERT a Lead

**Functionality**

"Upsert" \(update + insert\) will atomically do the following: 1. Check for the existence of a Lead matching certain criteria 1. If one exists, update it with the supplied parameters. 1. If not, create a new Lead with the supplied parameters. 1. This is particularly useful to avoid creating duplicate Leads.

**Match Criteria**

The supported match criteria are:

* Name
* Email
* Custom Fields

To match on a Custom Field, the corresponding Custom Field Definition must be available on Leads and included in filters. \(These settings may be viewed and edited in the web application via System Settings -&gt; Custom Fields.\)

**Match Outcomes**

Match outcomes are handled as follows:

* If no matches are found, create a new Lead.
* If exactly one match is found, update that Lead.
* If more than one match is found, return a 422 response with the IDs of the matching Leads.
* If more than 30 matches are found, return a 422 response without the IDs of the matching Leads.

`PUT {{base_url}}/leads/upsert`

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
  "properties": { 
    "name": "My Lead", 
    "email": { 
      "email": "mylead@gmail.test", 
      "category": "work" 
    } 
  }, 
  "match": { 
    "field_name": "email", 
    "field_value": "mylead@gmail.test" 
  } 
}
```

## Example Responses

* UPSERT a Lead

200: OK

```javascript
{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":128735,"value":null}],"date_created":1489531171,"date_modified":1512006056,"date_last_contacted":null}
```

