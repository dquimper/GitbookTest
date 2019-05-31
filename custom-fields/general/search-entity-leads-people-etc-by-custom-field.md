# Search Entity \(Leads, People, etc\) by Custom Field

Custom fields are available for each of the entities \(Leads, People, Companies, Opportunities, Projects, and Tasks\). Custom field types include: Text Field, Text Area, Dropdown, Date, Checkbox, Number Field, URL, Percentage, Currency, and Multi-Select Dropdown. Text fields are not searchable at this point. The table below summarizes the behavior of each of these fields.

| Field | Type | Search for Empty Value? | Any, All, None Options |
| :--- | :--- | :--- | :--- |
| Dropdown | integer array | Yes | No |
| Date | integer range | No | No |
| Checkbox | boolean | No | No |
| Number Field | numeric | No | No |
| Percentage | numeric range | No | No |
| Currency | integer range | No | No |
| Multi-Select Dropdown | integer array | Yes | Yes |

Except for text-related fields, each custom field can be searched via the dev API search endpoint for any of the entities. For Leads, this would be the endpoint `/leads/search`.

Dropdown and Multi-Select Dropdown fields have the additional option of searching for records where dropdown and multi-select dropdown fields are empty. This can be accomplished by adding an additional field: { "allow\_empty": true }. Searching by Multi-select dropdown also allows searching if any, all, or none of the dropdown options are to be searched. These options can be used together.

Examples of searching for each of the searchable fields can be found under the dropdown menu on the right. Examples given are for `Leads` and can be easily interchanged with any other entity.

`POST {{base_url}}/{{entity_name_in_plural}}/search`

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

* Search Custom Dropdown Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

* Search Custom Multi-Select Dropdown Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

* Search Custom Date Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

* Search Custom Multi-Select Dropdown Field for Both Set Value and Empty Value

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null},{"id":1,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":5000,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":10,"value":[]},{"custom_field_definition_id":2,"value":null},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":7,"value":null},{"custom_field_definition_id":5,"value":false},{"custom_field_definition_id":3,"value":null}],"date_created":1518656436,"date_modified":1518656436,"date_last_contacted":null}]
```

* Search Custom Dropdown Field for Empty Value

200: OK

```javascript
[{"id":1,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":5000,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":10,"value":[]},{"custom_field_definition_id":2,"value":null},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":7,"value":null},{"custom_field_definition_id":5,"value":false},{"custom_field_definition_id":3,"value":null}],"date_created":1518656436,"date_modified":1518656436,"date_last_contacted":null}]
```

* Search Custom Currency Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

* Search Custom Checkbox Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

* Search Custom Percentage Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

* Search Custom Number Field

200: OK

```javascript
[{"id":2,"name":"Jim Halpert (sample)","prefix":null,"first_name":"Jim Halpert (sample)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Scranton","state":"PA","postal_code":"18503","country":null},"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":1,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":null,"monetary_value":2500,"socials":[],"status":"New","status_id":1,"tags":["sample"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":1,"value":"Blah"},{"custom_field_definition_id":2,"value":"blah blah blah"},{"custom_field_definition_id":3,"value":1},{"custom_field_definition_id":4,"value":1518595200},{"custom_field_definition_id":5,"value":true},{"custom_field_definition_id":6,"value":42.0},{"custom_field_definition_id":7,"value":"http://blah.com"},{"custom_field_definition_id":8,"value":50},{"custom_field_definition_id":9,"value":1000.0},{"custom_field_definition_id":10,"value":[3]}],"date_created":1518656437,"date_modified":1518657195,"date_last_contacted":null}]
```

