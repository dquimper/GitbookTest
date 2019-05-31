# 4. Companies

A Company is an organization with which you communicate. The Companies API allows you to create, view, delete and update your Companies. You can retrieve individual Companies, list all Companies, or use search filters to view subsets of your Companies.

**Company Properties**

|                   Field                    |  Type   |                                      Details                                      |
| ------------------------------------------ | ------- | --------------------------------------------------------------------------------- |
| id                                         | number  | Unique identifier for the Company.                                                |
| name*                                      | string  | The name of the Company.                                                          |
| address                                    | address | An encapsulation of the Company's street, city, state, postal code, and country.  |
| assignee_id                                | number  | Unique identifier of the User that will be the owner of the Company.              |
| contact_type_id                            | number  | The unique identifier of the Contact Type of the Company.                         |
| details                                    | string  | Description of the Company.                                                       |
| email_domain                               | string  | The domain to which email addresses for the Company belong.                       |
| phone_numbers[]                            | list    | An array of phone numbers belonging to the Company.                               |
| phone_numbers[].number                     | string  | A phone number.                                                                   |
| phone_numbers[].category                   | string  | The category of the phone number.                                                 |
| socials[]                                  | list    | An array of social profiles belonging to the Company.                             |
| socials[].url                              | string  | The URL of a social profile.                                                      |
| socials[].category                         | string  | The category of the social profile.                                               |
| tags                                       | list    | An array of the tags associated with the Company, represented as strings.         |
| websites[]                                 | list    | An array of websites belonging to the Company.                                    |
| websites[].url                             | string  | The URL of a website.                                                             |
| websites[].category                        | string  | The category of the website.                                                      |
| date_created                               | number  | A Unix timestamp representing the time at which this Company was created.         |
| date_modified                              | number  | A Unix timestamp representing the time at which this Company was last modified.   |
| custom_fields[]                            | list    | An array of custom field values belonging to the Company.                         |
| custom_fields[].custom_field_definition_id | number  | The id of the Custom Field Definition for which this Custom Field stores a value. |
| custom_fields[].value                      | mixed   | The value (number, string, option id, or timestamp) of this Custom Field.         |
| \* indicates a required field | | |

*Please note that* ***email domain is a unique key*** *for Companies and no two records can have the same domain name. If you try to create a new Company with an existing email domain, then your request will fail.*