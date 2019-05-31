# 2. Leads

A Lead is an individual or a company that's interested in your products or services. It's a "catch-all" object that contains information about the contact, the company and the project in one. When Leads are qualified, they are usually converted to a Person, Company and Opportunity.

**Lead Properties**

|                   Field                    |     Type      |                                                     Details                                                     |
| ------------------------------------------ | ------------- | --------------------------------------------------------------------------------------------------------------- |
| id                                         | number        | Unique identifier for the Lead.                                                                                 |
| name*                                       | string        | The first and last name of the Lead.                                                                            |
| address                                    | address       | An encapsulation of the Lead's street, city, state, postal code, and country.                                   |
| assignee_id                                | number        | Unique identifier of the User that will be the owner of the Lead.                                               |
| company_name                               | string        | The name of the company to which the Lead belongs.                                                              |
| customer_source_id                         | number        | Unique identifier of the Customer Source that generated this Lead.                                              |
| details                                    | string        | Description of the Lead.                                                                                        |
| email                                      | email_address | An encapsulation of the Lead's email address and category.                                                      |
| monetary_value                             | number        | The expected monetary value of business with the Lead                                                           |
| phone_numbers[]                            | list          | An array of phone numbers belonging to the Lead.                                                                |
| phone_numbers[].number                     | string        | A phone number.                                                                                                 |
| phone_numbers[].category                   | string        | The category of the phone number.                                                                               |
| socials[]                                  | list          | An array of social profiles belonging to the Lead.                                                              |
| socials[].url                              | string        | The URL of a social profile.                                                                                    |
| socials[].category                         | string        | The category of the social profile.                                                                             |
| status                                     | string_enum   | A string representing the status of the Lead. Valid values are: "New", "Unqualified", "Contacted", "Qualified". |
| tags                                       | list          | An array of the tags associated with the Lead, represented as strings.                                          |
| title                                      | string        | The professional title of the Lead.                                                                             |
| websites[]                                 | list          | An array of websites belonging to the Lead.                                                                     |
| websites[].url                             | string        | The URL of a website.                                                                                           |
| websites[].category                        | string        | The category of the website.                                                                                    |
| custom_fields[]                            | list          | An array of custom field values belonging to the Lead.                                                          |
| custom_fields[].custom_field_definition_id | number        | The id of the Custom Field Definition for which this Custom Field stores a value.                               |
| custom_fields[].value                      | mixed         | The value (number, string, option id, or timestamp) of this Custom Field.                                       |
| date_created                               | number        | A Unix timestamp representing the time at which this Lead was created.                                          |
| date_modified                              | number        | A Unix timestamp representing the time at which this Lead was last modified.                                    |
|\* indicates a required field| | |