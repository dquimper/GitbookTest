# List Leads \(Search\)

The /search endpoint provides the ability to list Leads and sort the results by certain parameters. When multiple ciriteria are provided records meeting ALL criteria will be returned \(the filtering criteria have an 'AND' relationship\).

To see examples of search request using the various parameters, click on the `Leads Search` dropdown on the right. Certain fields can be filtered by an empty value, i.e., filter records where the field is not specified. For Leads, these fields are: city, state, postal\_code, tags, custom dropdown, custom multi-select fields. For an example of how this works, see `Search Leads by Empty Field`. Some fields \(e.g. assignee\_ids\) can also filter for an empty value by specifying -2 as the ID.

To search by custom fields, see `Search Entity by Custom Field` under `Custom Fields` folder.

To change the number of records returned, change the "page\_size" parameter. E.g., specify 200 for a page size of 200 records.

| Field | Type | Details | Default |
| :--- | :--- | :--- | :--- |
| page\_number | number | The page number \(starting with 1\) that you would like to view. | 1 |
| page\_size | number | The number of entries included in a page of results | 20 |
| sort\_by | string | The field on which to sort the results \(see footnote 1\). | name |
| sort\_direction | string | The direction in which to sort the results. Possible values are: asc or desc. | asc |
| name | string | Full name of the Lead to search for. | none |
| phone\_number | string | Phone number of the Lead to search for. | none |
| emails | string | Email of the Lead to search for. | none |
| assignee\_ids | number\[\] | The ids of Users that Leads are assigned to \(see footnote 2\). | none |
| status\_ids | number\[\] | An array of Lead status IDs \(see footnote 3\). | none |
| customer\_source\_ids | number\[\] | An array of customer source IDs \(see footnote 4\). | none |
| city | string | The city in which Leads must be located. | none |
| state | string | The state or province in which Leads must be located. | none |
| postal\_code | string | The postal code in which Leads must be located. | none |
| country | string | The two character country code where Leads must be located. | none |
| tags | string\[\] | Filter Leads to those that match at least one of the tags specified. | none |
| followed | number | 1: followed, 2: not followed | none |
| age | number | The maximum age in seconds that each Lead must be. | none |
| minimum\_monetary\_value | number | The minimum monetary value Leads must have. | none |
| maximum\_monetary\_value | number | The maximum monetary value Leads must have. | none |
| minimum\_interaction\_count | number | The minimum number of interactions Leads must have had. | none |
| maximum\_interaction\_count | number | The maximum number of interactions Leads must have had. | none |
| minimum\_interaction\_date | timestamp | The Unix timestamp of the earliest date of the last interaction. | none |
| maximum\_interaction\_date | timestamp | The Unix timestamp of the latest date of the last interaction. | none |
| minimum\_created\_date | timestamp | The Unix timestamp of the earliest date Leads are created. | none |
| maximum\_created\_date | timestamp | The Unix timestamp of the latest date Leads are created. | none |
| minimum\_modified\_date | timestamp | The Unix timestamp of the earliest date Leads are modified. | none |
| maximum\_modified\_date | timestamp | The Unix timestamp of the latest date Leads are modified. | none |

Foonotes: 1. Possible fields are: name, first\_name, last\_name, company\_name, title, value, email, phone, date\_modified, date\_created, city, state, country, zip, inactive\_days.

* date\_modified and date\_created: sorting is from oldest to newest
* inactive\_days: sorting is from newest to oldest
  1. To get User IDs, see `List Users` under `Acount and Users` folder. Enter -2 as an ID for no assignee.
  2. To get lead status IDs, see `List Lead Statuses` under `Other Resources` folder.
  3. To get customer source IDs, see `List Customer Sources` under `Other Resources` folder. Enter -2 as an ID for no customer source.

`POST {{base_url}}/leads/search`

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

* Search Leads by Phone Number

200: OK

```javascript
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 1,
        "monetary_unit": "USD",
        "monetary_value": 2500,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [
            "tag1"
        ],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
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
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1515800495,
        "date_last_contacted": 1515796263
    }
]
```

* Search Leads by Empty Field

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2501,"socials":[],"status":"New","status_id":5,"tags":["blah"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1516214189,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":6,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```

* Search Leads by Status Change Date

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```

* Search Leads by Followed

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```

* Search Leads by Custom Date Field

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[]}],"date_created":1515434872,"date_modified":1515800180,"date_last_contacted":1515796263}]
```

* Search Leads by Interaction Count

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```

* Leads Search

200: OK

```javascript
[{"id":9150547,"name":"My Contact","prefix":null,"first_name":"My","last_name":"Contact","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mycontact@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045162,"date_modified":1490045162},{"id":9150552,"name":"My Contact","prefix":null,"first_name":"My","last_name":"Contact","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":null,"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045237,"date_modified":1490045237},{"id":9150578,"name":"My Contact","prefix":null,"first_name":"My","last_name":"Contact","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":null,"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[{"number":"415-123-45678","category":"mobile"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1490045279,"date_modified":1490045279},{"id":8982554,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489528899,"date_modified":1489528899},{"id":8982702,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@gmail.test","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489531171,"date_modified":1489531171},{"id":9094361,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489791225,"date_modified":1489791225},{"id":9094364,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"123456789012345678901234567890"},{"custom_field_definition_id":103481,"value":"123456789012345678901234567890"}],"date_created":1489791283,"date_modified":1489791283},{"id":9094371,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------"},{"custom_field_definition_id":103481,"value":"123456789012345678901234567890"}],"date_created":1489791417,"date_modified":1489791417},{"id":9094372,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5-----"},{"custom_field_definition_id":103481,"value":"123456789012345678901234567890"}],"date_created":1489791453,"date_modified":1489791453},{"id":9094373,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5-----"},{"custom_field_definition_id":103481,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------"}],"date_created":1489791470,"date_modified":1489791470},{"id":9094383,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5-----"},{"custom_field_definition_id":103481,"value":"|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------|--------1---------2---------3---------4---------5---------6---------7---------8---------9---------"}],"date_created":1489791672,"date_modified":1489791672},{"id":9174441,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"text \n text"}],"date_created":1490112942,"date_modified":1490112942},{"id":9174443,"name":"My Lead","prefix":null,"first_name":"My","last_name":"Lead","middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":null,"customer_source_id":null,"details":null,"email":{"email":"mylead@noemail.com","category":"work"},"interaction_count":0,"monetary_value":null,"socials":[],"status":"New","status_id":208231,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":100764,"value":"Text fields are 255 chars or less!"},{"custom_field_definition_id":103481,"value":"text /n text"}],"date_created":1490112953,"date_modified":1490112953},{"id":8894157,"name":"Test Lead","prefix":null,"first_name":"Test","last_name":"Lead","middle_name":null,"suffix":null,"address":{"street":"301 Howard St Ste 600","city":"San Francisco","state":"CA","postal_code":"94105","country":"US"},"assignee_id":137658,"company_name":"Lead's Company","customer_source_id":331241,"details":"This is an update","email":{"email":"address@workemail.com","category":"work"},"interaction_count":0,"monetary_value":100,"socials":[{"url":"facebook.com/test_lead","category":"facebook"}],"status":"New","status_id":208231,"tags":["tag 1","tag 2"],"title":"Title","websites":[{"url":"www.workwebsite.com","category":"work"}],"phone_numbers":[{"number":"415-999-4321","category":"mobile"},{"number":"415-555-1234","category":"work"}],"custom_fields":[{"custom_field_definition_id":100764,"value":null},{"custom_field_definition_id":103481,"value":null}],"date_created":1489018784,"date_modified":1496692911}]
```

* Search Leads by Full Name

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1515800495,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":6,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```

* Search Leads by State

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```

* Search Leads by Tags

200: OK

```javascript
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 1,
        "monetary_unit": "USD",
        "monetary_value": 2501,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [
            "blah"
        ],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
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
            }
        ],
        "date_created": 1515434872,
        "date_modified": 1516214189,
        "date_last_contacted": 1515796263
    }
]
```

* Search Leads by Monetary Value

200: OK

```javascript
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": "USD",
        "monetary_value": 2500,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515795399,
        "date_last_contacted": null
    }
]
```

* Search Leads by Created Date

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```

* Search Leads by Custom Multi-Select Dropdown

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1515800495,"date_last_contacted":1515796263}]
```

* Search Leads by Email

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2501,"socials":[],"status":"New","status_id":5,"tags":["blah"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":12,"value":[8]}],"date_created":1515434872,"date_modified":1516214189,"date_last_contacted":1515796263}]
```

* Search Leads by Postal Code

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```

* Search Leads by Assignee IDs

200: OK

```text
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 2500,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515783705,
        "date_last_contacted": null
    }
]
```

* Search Leads by Custom Multi-Select Dropdown Set to Empty

200: OK

```javascript
[{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":6,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null}]
```

* Search Leads by Status IDs

200: OK

```javascript
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 2500,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515783705,
        "date_last_contacted": null
    },
    {
        "id": 5,
        "name": "Pam Beesly (sample)",
        "prefix": null,
        "first_name": "Pam Beesly (sample)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": null,
        "assignee_id": null,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!",
        "email": {
            "email": "pam@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 5000,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [
            "sample"
        ],
        "title": "Office Coordinator",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5105553333",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515525131,
        "date_last_contacted": null
    }
]
```

* List Leads in groups of 200

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2501,"socials":[],"status":"New","status_id":5,"tags":["blah"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[{"custom_field_definition_id":12,"value":[8]},{"custom_field_definition_id":6,"value":1515744000},{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434872,"date_modified":1516743967,"date_last_contacted":1515796263},{"id":5,"name":"Pam Beesly (sample)","prefix":null,"first_name":"Pam Beesly (sample)","last_name":null,"middle_name":null,"suffix":null,"address":null,"assignee_id":null,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!","email":{"email":"pam@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":5000,"socials":[],"status":"Unqualified","status_id":7,"tags":["sample"],"title":"Office Coordinator","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5105553333","category":"work"}],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1515434872,"date_modified":1515795399,"date_last_contacted":null},{"id":12,"name":"Test User","prefix":null,"first_name":"Test","last_name":"User","middle_name":null,"suffix":null,"address":{"street":"123 Abc Rd","city":"San Francisco","state":"CA","postal_code":"94114","country":""},"assignee_id":2,"company_name":null,"customer_source_id":null,"details":null,"email":null,"interaction_count":0,"monetary_unit":null,"monetary_value":null,"socials":[],"status":"New","status_id":5,"tags":[],"title":null,"websites":[],"phone_numbers":[],"custom_fields":[{"custom_field_definition_id":8,"value":null},{"custom_field_definition_id":11,"value":null},{"custom_field_definition_id":9,"value":null},{"custom_field_definition_id":7,"value":false},{"custom_field_definition_id":3,"value":null},{"custom_field_definition_id":4,"value":null},{"custom_field_definition_id":12,"value":[]},{"custom_field_definition_id":10,"value":null},{"custom_field_definition_id":6,"value":null},{"custom_field_definition_id":5,"value":null}],"date_created":1516671366,"date_modified":1516671455,"date_last_contacted":null}]
```

* Search Leads by Country

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```

* Search Leads by City

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":0,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515795800,"date_last_contacted":null}]
```

* Search Leads by Customer Source IDs

200: OK

```javascript
[
    {
        "id": 6,
        "name": "Jim Halpert (sample2)",
        "prefix": null,
        "first_name": "Jim Halpert (sample2)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": {
            "street": "213 West Main St",
            "city": "Philadelphia",
            "state": "PA",
            "postal_code": "18503",
            "country": "US"
        },
        "assignee_id": 2,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "This is an update",
        "email": {
            "email": "jim@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 2500,
        "socials": [],
        "status": "New",
        "status_id": 5,
        "tags": [],
        "title": "Manager",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5104447778",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515786833,
        "date_last_contacted": null
    },
    {
        "id": 5,
        "name": "Pam Beesly (sample)",
        "prefix": null,
        "first_name": "Pam Beesly (sample)",
        "last_name": null,
        "middle_name": null,
        "suffix": null,
        "address": null,
        "assignee_id": null,
        "company_name": "Dunder Mifflin, Inc.",
        "customer_source_id": 4,
        "details": "A Lead is someone you've qualified as a potential client. When you are ready to start making a deal, simply convert the Lead into an Opportunity.\n\nOnce your Lead becomes an Opportunity, you'll be able to track progress between each stage of the deal making process in your fully customizable Opportunity Pipeline. Add your own Lead and convert it to an Opportunity to see how it works!",
        "email": {
            "email": "pam@dundermifflin.com",
            "category": "work"
        },
        "interaction_count": 0,
        "monetary_unit": null,
        "monetary_value": 5000,
        "socials": [],
        "status": "Unqualified",
        "status_id": 7,
        "tags": [
            "sample"
        ],
        "title": "Office Coordinator",
        "websites": [
            {
                "url": "http://www.dundermifflin.com",
                "category": "work"
            }
        ],
        "phone_numbers": [
            {
                "number": "5105553333",
                "category": "work"
            }
        ],
        "custom_fields": [],
        "date_created": 1515434872,
        "date_modified": 1515525131,
        "date_last_contacted": null
    }
]
```

* Search Leads by Modified Date

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```

* Search Leads by Interaction Date

200: OK

```javascript
[{"id":6,"name":"Jim Halpert (sample2)","prefix":null,"first_name":"Jim Halpert (sample2)","last_name":null,"middle_name":null,"suffix":null,"address":{"street":"213 West Main St","city":"Philadelphia","state":"PA","postal_code":"18503","country":"US"},"assignee_id":2,"company_name":"Dunder Mifflin, Inc.","customer_source_id":4,"details":"This is an update","email":{"email":"jim@dundermifflin.com","category":"work"},"interaction_count":1,"monetary_unit":"USD","monetary_value":2500,"socials":[],"status":"New","status_id":5,"tags":["tag1"],"title":"Manager","websites":[{"url":"http://www.dundermifflin.com","category":"work"}],"phone_numbers":[{"number":"5104447778","category":"work"}],"custom_fields":[],"date_created":1515434872,"date_modified":1515796276,"date_last_contacted":1515796263}]
```

