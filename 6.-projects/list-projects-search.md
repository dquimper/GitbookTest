# List Projects \(Search\)

The /search endpoint provides the ability to list records and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned \(the filtering criteria have an 'AND' relationship\).

To see examples of search request using the various parameters, click on the `Projects Search` dropdown on the right. Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Projects, these fields are: tags, custom dropdown, custom multi-select fields. For an example of how this works, see `Search Project by Empty Field`. Some fields \(e.g. assignee\_ids\) can also filter for an empty value by specifying -2 as the ID.

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
| status\_ids | number\[\] | An array of Opportunity status IDs. | none |
| tags | string\[\] | Filter Opportunities to those that match at least one of the tags specified. | none |
| followed | number | 1: followed, 2: not followed | none |
| minimum\_created\_date | timestamp | The Unix timestamp of the earliest date Opportunities are created. | none |
| maximum\_created\_date | timestamp | The Unix timestamp of the latest date Opportunities are created. | none |
| minimum\_modified\_date | timestamp | The Unix timestamp of the earliest date Opportunities are modified. | none |
| maximum\_modified\_date | timestamp | The Unix timestamp of the latest date Opportunities are modified. | none |

Foonotes: 1. Possible fields are: name, assigned\_to, related\_to, status, date\_modified, date\_created.

`POST {{base_url}}/projects/search`

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

* Search Projects by Custom Multi-Select Dropdown Set to Empty

200: OK

```javascript
[{"id":2,"name":"Test Project","related_resource":null,"assignee_id":2,"status":"Open","details":null,"tags":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516751006,"date_modified":1516751006}]
```

* Projects Search

200: OK

```javascript
[
    {
        "id": 13358412,
        "name": "Demo Company",
        "address": {
            "street": "123 Main St",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": null
        },
        "assignee_id": null,
        "contact_type_id": null,
        "details": "This is a demo company",
        "email_domain": "democompany.com",
        "phone_numbers": [
            {
                "number": "415-123-45678",
                "category": "work"
            }
        ],
        "socials": [],
        "tags": [],
        "websites": [
            {
                "url": "http://democompany.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": null
            },
            {
                "custom_field_definition_id": 103481,
                "value": null
            }
        ],
        "interaction_count": 0,
        "date_created": 1496707930,
        "date_modified": 1496707932
    },
    {
        "id": 9607580,
        "name": "Dunder Mifflin (sample)",
        "address": {
            "street": "213 West Main Street",
            "city": "Scranton",
            "state": "PA",
            "postal_code": "18501",
            "country": ""
        },
        "assignee_id": null,
        "contact_type_id": null,
        "details": "This is an update",
        "email_domain": "dundermifflin.com",
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [],
        "tags": [],
        "websites": [
            {
                "url": "http://www.dundermifflin.com/index.shtml",
                "category": "work"
            },
            {
                "url": "https://www.nbcstore.com/shop-by-show/the-office.html?shop_by_theme=7",
                "category": "work"
            },
            {
                "url": "http://dundermifflin.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": null
            },
            {
                "custom_field_definition_id": 103481,
                "value": null
            }
        ],
        "interaction_count": 2,
        "date_created": 1483988828,
        "date_modified": 1496710807
    },
    {
        "id": 13362547,
        "name": "New Demo Opportunity",
        "address": null,
        "assignee_id": null,
        "contact_type_id": null,
        "details": null,
        "email_domain": null,
        "phone_numbers": [],
        "socials": [],
        "tags": [],
        "websites": [],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": null
            },
            {
                "custom_field_definition_id": 103481,
                "value": null
            }
        ],
        "interaction_count": 0,
        "date_created": 1496713616,
        "date_modified": 1496713616
    },
    {
        "id": 13362760,
        "name": "New Demo Project",
        "address": null,
        "assignee_id": null,
        "contact_type_id": null,
        "details": null,
        "email_domain": null,
        "phone_numbers": [],
        "socials": [],
        "tags": [],
        "websites": [],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": null
            },
            {
                "custom_field_definition_id": 103481,
                "value": null
            }
        ],
        "interaction_count": 0,
        "date_created": 1496713797,
        "date_modified": 1496713797
    },
    {
        "id": 13349319,
        "name": "Noemail",
        "address": null,
        "assignee_id": 137658,
        "contact_type_id": 451490,
        "details": null,
        "email_domain": "noemail.com",
        "phone_numbers": [],
        "socials": [],
        "tags": [],
        "websites": [],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": "Text fields are 255 chars or less!"
            },
            {
                "custom_field_definition_id": 103481,
                "value": "Text area fields can have long text content"
            }
        ],
        "interaction_count": 0,
        "date_created": 1496694264,
        "date_modified": 1496713841
    },
    {
        "id": 9607579,
        "name": "Copper",
        "address": {
            "street": "221 Main Street Suite 1350",
            "city": "San Francisco",
            "state": "CA",
            "postal_code": "94105",
            "country": ""
        },
        "assignee_id": null,
        "contact_type_id": 451493,
        "details": "Overview: ProsperWorks is the world's first zero input CRM. Designed specifically for Google Apps, ProsperWorks helps companies sell more faster by identifying, organizing and tracking sales opportunities right in Gmail, Calendar and Google Drive. By removing the need for data entry, salespeople can focus on developing business and managers can finally have accurate forecasting with real time activity tracking. ProsperWorks was founded by Jon Lee, Kelly Cheng and Andrew Hu with the commitment to empower small business sales and marketing. Jon was Founder/CEO of three big data companies that solved optimization problems in advertising, gaming and photo sharing. Each company realized successful exits. The team also includes the leaders in engineering and product from Facebook Mobile, BaseCRM and Salesforce. ProsperWorks has raised $10 million in funding from True Ventures, Bloomberg Beta, Crunchfund and other high-profile angel investors. ProsperWorks is based in San Francisco, CA.\n\nApprox. Number of Employees: 30\n\nFounded: 2011\n\nKeywords: Automotive, CRM, Finance, Google, Google Apps, Leadership, Management, Podcasting, SAAS, Sales, Small Business",
        "email_domain": "copper.com",
        "phone_numbers": [
            {
                "number": "4153554776",
                "category": "work"
            }
        ],
        "socials": [
            {
                "url": "https://www.linkedin.com/company/copper-inc-",
                "category": "linkedin"
            },
            {
                "url": "https://twitter.com/Copper",
                "category": "twitter"
            },
            {
                "url": "https://www.facebook.com/Copper",
                "category": "facebook"
            },
            {
                "url": "http://klout.com/Copper",
                "category": "klout"
            },
            {
                "url": "https://angel.co/copper",
                "category": "other"
            },
            {
                "url": "https://plus.google.com/u/0/103594665195397142807",
                "category": "other"
            },
            {
                "url": "http://www.crunchbase.com/organization/copper",
                "category": "other"
            }
        ],
        "tags": [],
        "websites": [
            {
                "url": "www.copper.com",
                "category": "work"
            },
            {
                "url": "https://www.copper.com",
                "category": "work"
            }
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": null
            },
            {
                "custom_field_definition_id": 103481,
                "value": null
            }
        ],
        "interaction_count": 0,
        "date_created": 1483988828,
        "date_modified": 1489018922
    },
    {
        "id": 9607581,
        "name": "Sabre Inc (sample)",
        "address": {
            "street": "543 Washington Ave",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "19135",
            "country": ""
        },
        "assignee_id": null,
        "contact_type_id": null,
        "details": null,
        "email_domain": null,
        "phone_numbers": [],
        "socials": [],
        "tags": [],
        "websites": [],
        "custom_fields": [
            {
                "custom_field_definition_id": 100764,
                "value": null
            },
            {
                "custom_field_definition_id": 103481,
                "value": null
            }
        ],
        "interaction_count": 0,
        "date_created": 1483988828,
        "date_modified": 1489018922
    }
]
```

* Search Projects by Tags

200: OK

```javascript
[
    {
        "id": 1,
        "name": "Customize Your New CRM",
        "related_resource": {
            "id": 2,
            "type": "company"
        },
        "assignee_id": 2,
        "status": "Open",
        "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
        "tags": [
            "tag1"
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            },
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
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516747365
    }
]
```

* Search Projects by Custom Multi-Select Dropdown

200: OK

```javascript
[
    {
        "id": 1,
        "name": "Customize Your New CRM",
        "related_resource": {
            "id": 2,
            "type": "company"
        },
        "assignee_id": 2,
        "status": "Open",
        "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
        "tags": [
            "tag1"
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            },
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
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516747365
    }
]
```

* Search Projects by Statuses

200: OK

```javascript
[
    {
        "id": 1,
        "name": "Customize Your New CRM",
        "related_resource": {
            "id": 2,
            "type": "company"
        },
        "assignee_id": 2,
        "status": "Open",
        "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
        "tags": [
            "tag1"
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            },
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
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516747365
    }
]
```

* List Projects in Groups of 200

200: OK

```javascript
[
    {
        "id": 1,
        "name": "Customize Your New CRM",
        "related_resource": {
            "id": 2,
            "type": "company"
        },
        "assignee_id": 2,
        "status": "Open",
        "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
        "tags": [
            "tag1"
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            },
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
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516819000
    },
    {
        "id": 2,
        "name": "Test Project",
        "related_resource": null,
        "assignee_id": 2,
        "status": "Open",
        "details": null,
        "tags": [],
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
        ],
        "date_created": 1516751006,
        "date_modified": 1516751006
    }
]
```

* Search Projects by Assignee Ids

200: OK

```javascript
[
    {
        "id": 1,
        "name": "Customize Your New CRM",
        "related_resource": {
            "id": 2,
            "type": "company"
        },
        "assignee_id": 2,
        "status": "Open",
        "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
        "tags": [
            "tag1"
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            },
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
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516747365
    }
]
```

* Search Projects by Custom Date Field

200: OK

```javascript
[
    {
        "id": 1,
        "name": "Customize Your New CRM",
        "related_resource": {
            "id": 2,
            "type": "company"
        },
        "assignee_id": 2,
        "status": "Open",
        "details": "Visit our settings section to discover all the ways you can customize Copper to fit your sales workflow.",
        "tags": [
            "tag1"
        ],
        "custom_fields": [
            {
                "custom_field_definition_id": 6,
                "value": 1515744000
            },
            {
                "custom_field_definition_id": 12,
                "value": [
                    8
                ]
            },
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
                "custom_field_definition_id": 10,
                "value": null
            },
            {
                "custom_field_definition_id": 5,
                "value": null
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516747365
    }
]
```

