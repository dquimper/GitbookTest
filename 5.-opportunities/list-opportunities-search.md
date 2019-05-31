# List Opportunities \(Search\)

The /search endpoint provides the ability to list records and sort the results by certain parameters. When multiple ciriteria are provided then records meeting ALL criteria will be returned \(the filtering criteria have an 'AND' relationship\).

To see examples of search request using the various parameters, click on the `Opportunities Search` dropdown on the right.Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Opportunities, these fields are: company\_ids, tags, custom dropdown, custom multi-select fields. For an example of how this works, see `Search Opportunities by Empty Field`. Some fields \(e.g. assignee\_ids\) can also filter for an empty value by specifying -2 as the ID.

To search by custom fields, see `Search Entity by Custom Field` under `Custom Fields` folder.

To change the number of records returned, change the "page\_size" parameter. E.g., specify 200 for a page size of 200 records.

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| page\_number | number | The page number \(starting with 1\) that you would like to view. | 1 |
| page\_size | number | The number of entries included in a page of results | 20 |
| sort\_by | string | The field on which to sort the results \(see footnote 1\). | name |
| sort\_direction | string | The direction in which to sort the results. Possible values are: asc or desc. | asc |
| name | string | Full name of the Opportunity to search for. | none |
| assignee\_ids | number\[\] | The ids of Users that Opportunities must be owned by, or -2 for Opportunities with no owner. | none |
| status\_ids | number\[\] | An array of Opportunity status IDs as integers. The integer values are 0, 1, 2, 3, for "Open", "Won", "Lost", and "Abandoned", respectively. | none |
| pipeline\_ids | number\[\] | An array of pipeline IDs. | none |
| pipeline\_stage\_ids | number\[\] | An array of pipeline stage IDs. | none |
| priority\_ids | number\[\] | An array of priority IDs. | none |
| customer\_source\_ids | number\[\] | An array of customer source IDs, or -2 for no customer source. | none |
| loss\_reason\_ids | number\[\] | An array of loss reason IDs, or -2 for no loss reason. | none |
| company\_ids | number\[\] | An array of company IDs. | none |
| tags | string\[\] | Filter Opportunities to those that match at least one of the tags specified. | none |
| followed | number | 1: followed, 2: not followed | none |
| minimum\_monetary\_value | number | The minimum monetary value Opportunities must have. | none |
| maximum\_monetary\_value | number | The maximum monetary value Opportunities must have. | none |
| minimum\_interaction\_count | number | The minimum number of interactions Opportunities must have had. | none |
| maximum\_interaction\_count | number | The maximum number of interactions Opportunities must have had. | none |
| minimum\_close\_date | timestamp | The Unix timestamp of the earliest close date. | none |
| maximum\_close\_date | timestamp | The Unix timestamp of the latest close date. | none |
| minimum\_interaction\_date | timestamp | The Unix timestamp of the earliest date of the last interaction. | none |
| maximum\_interaction\_date | timestamp | The Unix timestamp of the latest date of the last interaction. | none |
| minimum\_stage\_change\_date | timestamp | The Unix timestamp of the earliest date of a state change. | none |
| maximum\_stage\_change\_date | timestamp | The Unix timestamp of the latest date of a state change. | none |
| minimum\_created\_date | timestamp | The Unix timestamp of the earliest date Opportunities are created. | none |
| maximum\_created\_date | timestamp | The Unix timestamp of the latest date Opportunities are created. | none |
| minimum\_modified\_date | timestamp | The Unix timestamp of the earliest date Opportunities are modified. | none |
| maximum\_modified\_date | timestamp | The Unix timestamp of the latest date Opportunities are modified. | none |

Foonotes: 1. Possible fields are: name, account, company\_name, value, assignee, customer\_source\_id, date\_modified, date\_created, contact, stage, status, close\_date, source, priority, last\_interaction, interaction\_count, deal\_last\_stage, win\_probability.

`POST {{base_url}}/opportunities/search`

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

* Search Opportunities by Multi-Select Dropdown Set to Empty

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516736722,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":3,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/22/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":5,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":3,"priority":"High","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":250000,"win_probability":5,"date_stage_changed":1515434867,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434867,"date_modified":1516736704,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":6,"name":"Sell stuff","assignee_id":null,"close_date":"2/8/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":5,"details":null,"loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":6,"priority":"None","status":"Lost","tags":[],"interaction_count":0,"monetary_unit":null,"monetary_value":null,"win_probability":5,"date_stage_changed":1515458602,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515458602,"date_modified":1516736700,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Interaction Count

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":2,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":1516737600,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516737667,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Company Ids

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516310945,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":3,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/22/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":5,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":3,"priority":"High","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":250000,"win_probability":5,"date_stage_changed":1515434867,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434867,"date_modified":1516673603,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Close Date

200: OK

```javascript
[{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516673290,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* List Opportunities in Groups of 200

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":2,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":1516737600,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516820005,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":["tag1"],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516736568,"custom_fields":[{"custom_field_definition_id":5,"value":6},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null}]},{"id":3,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/22/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":5,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":3,"priority":"High","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":250000,"win_probability":5,"date_stage_changed":1515434867,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434867,"date_modified":1516736704,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":6,"name":"Sell stuff","assignee_id":null,"close_date":"2/8/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":5,"details":null,"loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":6,"priority":"None","status":"Lost","tags":[],"interaction_count":0,"monetary_unit":null,"monetary_value":null,"win_probability":5,"date_stage_changed":1515458602,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515458602,"date_modified":1516736700,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Date Stage Changed

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":2,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":1516737600,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516737667,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Priorities

200: OK

```javascript
[{"id":3,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/22/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":5,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":3,"priority":"High","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":250000,"win_probability":5,"date_stage_changed":1515434867,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434867,"date_modified":1516673603,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Custom Multi-Select Dropdown

200: OK

```javascript
[{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":["tag1"],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516736568,"custom_fields":[{"custom_field_definition_id":5,"value":6},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null}]}]
```

* Search Opportunities by Date Last Interacted

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":2,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":1516737600,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516737667,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Pipeline Stage Ids

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516310945,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Value

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516310945,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Tags

200: OK

```javascript
[{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":["tag1"],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516736568,"custom_fields":[{"custom_field_definition_id":5,"value":6},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null}]}]
```

* Search Opportunities by Custom Date Field

200: OK

```javascript
[{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":["tag1"],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516736568,"custom_fields":[{"custom_field_definition_id":5,"value":6},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null}]}]
```

* Opportunities Search

200: OK

```javascript
[{"id":2827699,"name":"25 Office Chairs (sample)","assignee_id":null,"close_date":"1/16/2017","company_id":9607580,"company_name":"Dunder Mifflin (sample)","customer_source_id":331242,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987793,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":75000,"win_probability":40,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1483988829,"date_modified":1489018922,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]},{"id":2827700,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/14/2017","company_id":9607581,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987791,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":50000,"win_probability":10,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1483988829,"date_modified":1496943803,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]},{"id":2827698,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/23/2017","company_id":9607580,"company_name":"Dunder Mifflin (sample)","customer_source_id":331241,"details":"This is an update","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":250000,"win_probability":5,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1483988829,"date_modified":1496776255,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]},{"id":3826510,"name":"Demo Opportunity","assignee_id":null,"close_date":null,"company_id":null,"company_name":null,"customer_source_id":null,"details":null,"loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":null,"win_probability":5,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1490114507,"date_modified":1496700017,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]},{"id":4417020,"name":"Demo Project","assignee_id":null,"close_date":null,"company_id":13349319,"company_name":"Noemail","customer_source_id":null,"details":"","loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":27140359,"priority":null,"status":"Open","tags":[],"interaction_count":1,"monetary_value":1000,"win_probability":0,"date_last_contacted":1496703593,"leads_converted_from":[{"lead_id":11393303,"converted_timestamp":1496694264}],"date_lead_created":1496692663,"date_created":1496694264,"date_modified":1496943309,"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"Text area fields can have long text content"},{"custom_field_definition_id":126240,"value":null}]},{"id":2841646,"name":"ejfpvoiewjrvoierjvoierv","assignee_id":137658,"close_date":"2/10/2017","company_id":null,"company_name":null,"customer_source_id":null,"details":null,"loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":null,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":null,"win_probability":5,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1484096886,"date_modified":1489018921,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]},{"id":4418567,"name":"New Demo Opportunity","assignee_id":null,"close_date":null,"company_id":13349319,"company_name":"Noemail","customer_source_id":null,"details":null,"loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":27140359,"priority":"None","status":"Open","tags":[],"interaction_count":1,"monetary_value":null,"win_probability":5,"date_last_contacted":1496703593,"leads_converted_from":[],"date_lead_created":null,"date_created":1496713840,"date_modified":1496943302,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]},{"id":4956209,"name":"New Demo Opportunity","assignee_id":null,"close_date":null,"company_id":13349319,"company_name":"Noemail","customer_source_id":331242,"details":null,"loss_reason_id":null,"pipeline_id":213214,"pipeline_stage_id":987790,"primary_contact_id":27140359,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_value":null,"win_probability":5,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1502158599,"date_modified":1502158600,"custom_fields":[{"custom_field_definition_id":126240,"value":null},{"custom_field_definition_id":103481,"value":null},{"custom_field_definition_id":100764,"value":null}]}]
```

* Search Opportunities by Created Date

200: OK

```javascript
[{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516673290,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Assignee Ids

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516310945,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Loss Reason Ids

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516310945,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516673290,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":3,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/22/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":5,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":3,"priority":"High","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":250000,"win_probability":5,"date_stage_changed":1515434867,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434867,"date_modified":1516673603,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":6,"name":"Sell stuff","assignee_id":null,"close_date":"2/8/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":5,"details":null,"loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":6,"priority":"None","status":"Lost","tags":[],"interaction_count":0,"monetary_unit":null,"monetary_value":null,"win_probability":5,"date_stage_changed":1515458602,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515458602,"date_modified":1516733449,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Statuses

200: OK

```javascript
[
    {
        "id": 4,
        "name": "25 Office Chairs (sample)",
        "assignee_id": 2,
        "close_date": "1/15/2018",
        "company_id": 3,
        "company_name": "Dunder Mifflin (sample)",
        "customer_source_id": 6,
        "details": "Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.",
        "loss_reason_id": null,
        "pipeline_id": 3,
        "pipeline_stage_id": 13,
        "primary_contact_id": 5,
        "priority": "None",
        "status": "Open",
        "tags": [],
        "interaction_count": 0,
        "monetary_unit": "USD",
        "monetary_value": 75000,
        "win_probability": 40,
        "date_stage_changed": 1515434869,
        "date_last_contacted": null,
        "leads_converted_from": [],
        "date_lead_created": null,
        "date_created": 1515434869,
        "date_modified": 1516310945,
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ]
    },
    {
        "id": 5,
        "name": "500 Keyboards (sample)",
        "assignee_id": null,
        "close_date": "1/13/2018",
        "company_id": 4,
        "company_name": "Sabre Inc (sample)",
        "customer_source_id": null,
        "details": "Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.",
        "loss_reason_id": null,
        "pipeline_id": 3,
        "pipeline_stage_id": 11,
        "primary_contact_id": 3,
        "priority": "None",
        "status": "Open",
        "tags": [],
        "interaction_count": 0,
        "monetary_unit": "USD",
        "monetary_value": 50000,
        "win_probability": 10,
        "date_stage_changed": 1515434870,
        "date_last_contacted": null,
        "leads_converted_from": [],
        "date_lead_created": null,
        "date_created": 1515434870,
        "date_modified": 1516673290,
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ]
    },
    {
        "id": 3,
        "name": "8 New Copy Machines (sample)",
        "assignee_id": null,
        "close_date": "1/22/2018",
        "company_id": 3,
        "company_name": "Dunder Mifflin (sample)",
        "customer_source_id": 5,
        "details": "Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.",
        "loss_reason_id": null,
        "pipeline_id": 3,
        "pipeline_stage_id": 10,
        "primary_contact_id": 3,
        "priority": "None",
        "status": "Open",
        "tags": [],
        "interaction_count": 0,
        "monetary_unit": "USD",
        "monetary_value": 250000,
        "win_probability": 5,
        "date_stage_changed": 1515434867,
        "date_last_contacted": null,
        "leads_converted_from": [],
        "date_lead_created": null,
        "date_created": 1515434867,
        "date_modified": 1516673297,
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ]
    },
    {
        "id": 6,
        "name": "Sell stuff",
        "assignee_id": null,
        "close_date": "2/8/2018",
        "company_id": 4,
        "company_name": "Sabre Inc (sample)",
        "customer_source_id": null,
        "details": null,
        "loss_reason_id": null,
        "pipeline_id": 3,
        "pipeline_stage_id": 10,
        "primary_contact_id": 6,
        "priority": "None",
        "status": "Open",
        "tags": [],
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": null,
        "win_probability": 5,
        "date_stage_changed": 1515458602,
        "date_last_contacted": null,
        "leads_converted_from": [],
        "date_lead_created": null,
        "date_created": 1515458602,
        "date_modified": 1516673280,
        "custom_fields": [
            {
                "custom_field_definition_id": 8,
                "value": null
            },
            {
                "custom_field_definition_id": 11,
                "value": null
            },
            {
                "custom_field_definition_id": 9,
                "value": null
            },
            {
                "custom_field_definition_id": 7,
                "value": false
            },
            {
                "custom_field_definition_id": 3,
                "value": null
            },
            {
                "custom_field_definition_id": 4,
                "value": null
            },
            {
                "custom_field_definition_id": 12,
                "value": []
            },
            {
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 6,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ]
    }
]
```

* Search Opportunities by Name

200: OK

```javascript
[{"id":4,"name":"25 Office Chairs (sample)","assignee_id":2,"close_date":"1/15/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":6,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":13,"primary_contact_id":5,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":75000,"win_probability":40,"date_stage_changed":1515434869,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434869,"date_modified":1516310945,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Customer Source Ids

200: OK

```javascript
[{"id":3,"name":"8 New Copy Machines (sample)","assignee_id":null,"close_date":"1/22/2018","company_id":3,"company_name":"Dunder Mifflin (sample)","customer_source_id":5,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":3,"priority":"High","status":"Open","tags":[],"interaction_count":0,"monetary_unit":"USD","monetary_value":250000,"win_probability":5,"date_stage_changed":1515434867,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434867,"date_modified":1516673603,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]},{"id":6,"name":"Sell stuff","assignee_id":null,"close_date":"2/8/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":5,"details":null,"loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":10,"primary_contact_id":6,"priority":"None","status":"Open","tags":[],"interaction_count":0,"monetary_unit":null,"monetary_value":null,"win_probability":5,"date_stage_changed":1515458602,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515458602,"date_modified":1516674120,"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}]}]
```

* Search Opportunities by Followed

200: OK

```javascript
[{"id":5,"name":"500 Keyboards (sample)","assignee_id":null,"close_date":"1/13/2018","company_id":4,"company_name":"Sabre Inc (sample)","customer_source_id":null,"details":"Opportunities are created for People and Companies that are interested in buying your products or services. Create Opportunities for People and Companies to move them through one of your Pipelines.","loss_reason_id":null,"pipeline_id":3,"pipeline_stage_id":11,"primary_contact_id":3,"priority":"None","status":"Open","tags":["tag1"],"interaction_count":0,"monetary_unit":"USD","monetary_value":50000,"win_probability":10,"date_stage_changed":1515434870,"date_last_contacted":null,"leads_converted_from":[],"date_lead_created":null,"date_created":1515434870,"date_modified":1516736568,"custom_fields":[{"custom_field_definition_id":5,"value":6},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null}]}]
```

