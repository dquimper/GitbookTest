# 3. People

A Person is an individual with whom you communicate. The People API allows you to create, view, delete and update your People. You can retrieve individual People, list all People, or use search filters to view subsets of your People.

**Person Properties**

|            Field            |  Type   |                                      Details                                      |
| --------------------------- | ------- | --------------------------------------------------------------------------------- |
| id                          | number  | Unique identifier for the Person.                                                 |
| name*                        | string  | The first and last name of the Person.                                            |
| address                     | address | An encapsulation of the Person's street, city, state, postal code, and country.   |
| assignee_id                 | number  | Unique identifier of the User that will be the owner of the Person.               |
| company_id                  | string  | The unique identifier of the primary Company with which the Person is associated. |
| company_name                | string  | The name of the primary Company with which the Person is associated.              |
| contact_type_id             | number  | The unique identifier of the Contact Type of the Person.                          |
| details                     | string  | Description of the Person.                                                        |
| emails[]                    | list    | An array of email addresses belonging to the Person.                              |
| emails[].email              | string  | An email address.                                                                 |
| emails[].category           | string  | The category of the email address.                                                |
| phone_numbers[]             | list    | An array of phone numbers belonging to the Person.                                |
| phone_numbers[].number      | string  | A phone number.                                                                   |
| phone_numbers[].category    | string  | The category of the phone number.                                                 |
| socials[]                   | list    | An array of social profiles belonging to the Person.                              |
| socials[].url               | string  | The URL of a social profile.                                                      |
| socials[].category          | string  | The category of the social profile.                                               |
| tags                        | list    | An array of the tags associated with the Person, represented as strings.          |
| title                       | string  | The professional title of the Person.                                             |
| websites[]                  | list    | An array of websites belonging to the Person.                                     |
| websites[].url              | string  | The URL of a website.                                                             |
| websites[].category         | string  | The category of the website.                                                      |
| date_created                | number  | A Unix timestamp representing the time at which this Person was created.          |
| date_modified               | number  | A Unix timestamp representing the time at which this Person was last modified.    |
| custom_fields[]             | list    | An array of custom field values belonging to the Person.                          |
| custom_fields[]             |         |                                                                                   |
| .custom_field_definition_id | number  | The id of the Custom Field Definition for which this Custom Field stores a value. |
| custom_fields[]             |         |                                                                                   |
| .value                      | mixed   | The value (number, string, option id, or timestamp) of this Custom Field.         |
| \* indicates a required field | | |

*Please note that* ***email address is a unique key*** *for People and no two records can have the same email address. If you try to create a new Person with an existing email address, then your request will fail.*