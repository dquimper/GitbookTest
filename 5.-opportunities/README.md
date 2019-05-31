# 5. Opportunities

An Opportunity is a potential business deal. The Opportunities API allows you to create, view, delete and update your Opportunities. You can retrieve individual Opportunities, list all Opportunities, or use search filters to view subsets of your Opportunities.

**Opportunity Properties**

|                   Field                    |    Type     |                                                         Details                                                          |
| ------------------------------------------ | ----------- | ------------------------------------------------------------------------------------------------------------------------ |
| id                                         | number      | Unique identifier for the Opportunity.                                                                                   |
| name*                                      | string      | The name of the Opportunity.                                                                                             |
| assignee_id                                | number      | Unique identifier of the User that will be the owner of the Opportunity.                                                 |
| close_date                                 | string      | The expected close date of the Opportunity in MM/DD/YYYY or DD/MM/YYYY format.                                           |
| company_id                                 | string      | The unique identifier of the primary Company with which the Opportunity is associated.                                   |
| company_name                               | string      | The name of the primary Company with which the Opportunity is associated.                                                |
| customer_source_id                         | number      | Unique identifier of the Customer Source that generated this Opportunity.                                                |
| details                                    | string      | Description of the Opportunity.                                                                                          |
| loss_reason_id                             | number      | If the Opportunity's status is "Lost", the unique identifier of the loss reason that caused this Opportunity to be lost. |
| monetary_value                             | number      | The monetary value of the Opportunity.                                                                                   |
| pipeline_id                                | number      | The unique identifier of the Pipeline in which this Opportunity is.                                                      |
| primary_contact_id*                        | number      | The unique identifier of the Person who is the primary contact for this Opportunity.                                     |
| priority                                   | string_enum | The priority of the Opportunity. Valid values are: "None", "Low", "Medium", "High".                                      |
| pipeline_stage_id                          | number      | The unique identifier of the Pipeline Stage of the Opportunity.                                                          |
| status                                     | string_enum | The status of the Opportunity. Valid values are: "Open", "Won", "Lost", "Abandoned".                                     |
| tags                                       | list        | An array of the tags associated with the Opportunity, represented as strings.                                            |
| win_probability                            | number      | The expected probability of winning the Opportunity. Valid values are [0-100] (inclusive).                               |
| date_created                               | number      | A Unix timestamp representing the time at which this Opportunity was created.                                            |
| date_modified                              | number      | A Unix timestamp representing the time at which this Opportunity was last modified.                                      |
| custom_fields[]                            | list        | An array of custom field values belonging to the Opportunity.                                                            |
| custom_fields[].custom_field_definition_id | number      | The id of the Custom Field Definition for which this Custom Field stores a value.                                        |
| custom_fields[].value                      | mixed       | The value (number, string, option id, or timestamp) of this Custom Field.                                                |
| \* indicates a required field | | |