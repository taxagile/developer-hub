<img src="../../docs/Tax_Agile_Logo_White_on_Purple.png" width="80">

[Home](../../README.md) \| [Getting started](../getting-started.md)  \|  [Postman](../postman.md) \| [Swagger](../swagger/index.html) \| [Change log](../changelog.md) \| [Coming soon](../coming-soon.md)

# VAT Filer via API - Overview
This page provides a high-level overview of the endpoints which support the VAT Filer product when working over the RESTful API. There are some dependencies and sequencing which are helpful to understand from the start. 

## Filings
VAT Filer prepares _filings_ and so _filings_ are the main RESTful resource within this API, and is located under the filer root and the VAT sub-route:

```GET /v0/filer/vat/filings ```

This resource it is not the kind of resource which accepts CRUD operations, you don't POST to create a filing that would be the wrong way to think of it. Instead firstly think of this endpoint providing _capabilities_ of the VAT Filer product, which is to say, that the resource here is "Filings which VAT Filer is capable of preparing".  

> *Capabilities*
>
> These _filings_ are the basis for setting up a Filing Event to be prepared (which is done via `/companies`); to be clear this endpoint **isn't** showing the filings active for your companies, instead it is showing the filings available, which provides you the information you need to  setup the Filing against the VAT Registrations in your companies.

*Sample Response*

Is a paginated list of filings using the standard `count, data, next` pattern:
```json 
{
    "count": 163,
    "data": [
        {
            "_id": "1CbBkT8GufLXR7QyM2eB",
            "countryCode": "AT",
            "name": "VAT Return (U 30)",
            "category": "VAT Return",
            "dueDate": {
                "months": 0,
                "days": 10
            },
            "frequencies": [
                "month"
            ]
        },
        { ... }
    ],
    "next": {
        "page": 2,
        "pageSize": 10,
        "href": "/v0/filer/vat/filings?page2&pageSize=10"
    }
}
```
The response returns key information which is required in subsequent VAT Filer API requests: 

| Key | Usage |
|:------|:--- |
| `_id` | The unique id of this particular filing, it is required as a path parameter in many other endpoints. |
| `frequencies` | An array of allowed values to be set for this filing frequency. |
| `dueDate` | Object includes the filing due date values; knowing these you can set an offset on the companies if you want to set the deadline earlier or later. |

*Request*

The request can also take query parameters to control the results returned for example: 

```GET /v0/filer/vat/filings?pageSize=20&page=2 ```

```GET /v0/filer/vat/filings?countryCode=BE ```

The category of filing can also be used, these are lowercased and hyphen in place of spaces, for example: 

```GET /v0/filer/vat/filings?category=vat-return```

These query parameters can be used in compound: 

```GET /v0/filer/vat/filings?pageSize=20&category=vat-return ```

```GET /v0/filer/vat/filings?pageSize=20&category=vat-return&countryCode=PL ```

## Companies
Having used the filings resource to understand the capabilities of VAT Filer, the next task is to setup a Filing and this is done within the `companies/` resource, as the obligation to make a filing is owned by the company and their VAT registrations.

This is a snippet of a request body for ``` POST /v0/companies ``` which is providing values from the previous endpoint, to setup the AT VAT Return within the `filings` array `[]`: 

```json
{
    "name": "Company test",
    "companyCode": "companyTest",
    "establishedCountry": "BE",
    "type": "Taxable person",
    "contacts": [],
    "locations": [],
    "domains": [
        {
            "domainId": "vat",
            "registrations": [
                {
                    "country": "PL",
                    "registrationId": "444455555",
                    "vatRegistrationType": "mainEstablishment",
                    "filings": [
                        {
                            "name": "VAT Return (JPK_V7M / JPK_V7K)",
                            "country": "PL",
                            "filingId": "6lxvlAsBZikljpKymB5R",
                            "frequency": "month",
                            "deadlineExtendedByDays": 0,
                            "deadlineExtendedByMonths": 0
                        }
                    ]
                }
            ]
        }
    ]
}
```

## Events
Bring together a filing obligation and a company, you get Filing Events which are provided on the following endpoint: 

``` GET /v0/filer/vat/filings/events?company=<id>&page=1&pageSize=10 ```

Where a company ID is mandatory.

> **Note: This route is changing in the next Release!** 
> 
> It will become ```GET /v0/filer/vat/filings/events/companies/:id```
> 
> To be more consistent with the other endpoints in the VAT Filer set. The response body is also expected to change, but the use-case it serves will remain the same, so the current example does provide a preview of future behaviour - but expect response body to follow the standard `count, data, next` paginated pattern and some events attributes may be added or removed.

*Sample Response*

_Note: The format of this response is changing in the next Release!_

```json
{
    "filings": [
        {
            "filingId": "6lxvlAsBZikljpKymB5R",
            "formName": "JPK_V7M / JPK_V7K",
            "country": "PL",
            "type": "VAT Return",
            "periodKey": "11-2025",
            "companyId": "<id>",
            "companyName": "TESTCOMP",
            "preparer": "",
            "reviewer": "",
            "submitter": "",
            "status": "Open",
            "dueDate": "2025-12-25",
            "href": "/v0/filer/vat/filings/events/companies/:id/filings/6lxvlAsBZikljpKymB5R/periods/11-2025/reports"
        }
    ],
    "count": {
        "totalEvents": 1,
        "showing": 1
    },
    "first": {
        "page": 1,
        "pageSize": 10,
        "href": "/v0/filer/vat/filings/events?company=<id>&page=1&pageSize=10"
    }
}
```
This is an instance of the Filing Event, which has the combination of company ID, the filing ID and the period key, these three values uniquely identify the specific filing and is used next to fetch the reports that show data loaded.

## Reports
Following the resource hierarchy, the `href` provided in the previous request points to the `reports` resource:

``` GET /v0/filer/vat/filings/events/companies/:id/filings/:id/periods/:id/reports ```

For example, for a specific combination of `events`
* where `companies/UNOUG5tXvJgeac3nIACm` and 
* where `filings/6lxvlAsBZikljpKymB5R` and 
* where `periods/11-2025`

The request:

``` GET /v0/filer/vat/filings/events/companies/UNOUG5tXvJgeac3nIACm/filings/6lxvlAsBZikljpKymB5R/periods/11-2025/reports ```

### reports/:id
The `/reports` resource takes a path parameter (`:id`) which is an enumeration of available reports; which are sub-resources, which have differing capabilities lower down the path hierarchy depending on the report id value:

| Value | Usage | 
|:----- | :---- |
| `view` | An HTML view of the filing, populated with box values over a background image. Ideal for presenting to users for confirmation of the filing data. |
| `filing` | The actual filing in an official submittable format as mandated by the Tax Authority. This can be a combination of filing data from upload _plus_ answers to specific filing questions. |

The up-to-date list of values is available from a helper endpoint: 

``` GET /v0/filer/vat/filings/events/companies/:id/filings/:id/periods/:id/reports ```

### reports/view
The `/view` report endpoint returns a visual of the Filing in HTML format.

``` GET /v0/filer/vat/filings/events/companies/:id/filings/:id/periods/:id/reports/view ```

Where multiple languages are supported in the report they can be provided as 3-digit language values in the `lang` query parameter:

``` GET /v0/filer/vat/filings/events/companies/:id/filings/:id/periods/:id/reports/view?lang=eng ```

_Note: A future iteration will provide a helper endpoint to list the available languages for a specific view._

### reports/filing
The `/filing` report endpoint deviates a little from RESTful convention (for good reason) so the specifics are carefully documented here.

Firstly, it is not possible to simply GET `../reports/filing` and expect the filing report to be returned as a response. This is because the process of creating an official filing usually contains the requirement to answer questions as part of the submittable format. 

The first step is to fetch filing metadata, providing a query parameter of the formatting wanted (for example, 'xml' or 'csv'):

#### GET /reports/filing/metadata
``` GET /v0/filer/vat/filings/events/companies/:id/filings/:id/periods/:id/reports/filing/metadata?format=xml ```

_Note: A future iteration will provide a helper endpoint to list the available formats for a specific filing._

The filing/metadata resource returns attributes about this filing, the prime attribute is the array of `"questions": []`

For example: 
```json
{
    "format": "xml",
    "questions": [
        {
            "id": "indicate-the-type-of-return",
            "sectionIndex": 0,
            "orderIndex": 0,
            "required": false,
            "label": "Indicate the type of return",
            "type": "select",
            "options": [
                "Regular submission",
                "Correction"
            ],
            "previousAnswer": "Regular submission",
        },
        { ... }
    ]
}
```

**Questions**

| Key | Usage |
|:----- | :---- |
| `id` | Unique identifier which is then used when providing the answer. |
| `sectionIndex` | Not fully implemented, automatic numbering is generated. | 
| `orderIndex` | Not fully implemented, automatic numbering is generated. |
| `previousAnswer` | If this combination of company and filing has been answered before, the previously supplied answer is provided as the user may want to answer the same as they did in their last filing. |
| `required` | Currently unused, defaults to false. |
| `label` | The label of the form field to ask this question to the user. |
| `type` | Values: `text`, `number`, `date`, `select` or `boolean`. |
| `options` | If the `type` is a `select` then the `options` array is a set of possible values for the answer. |

Having received the questions for the filing, the API caller should prompt the user for answers to these questions. When the user has provided answers, then the API caller should submit the answers as part of the POST `/reports/filing` request body to then get the submittable filing as the _synchronous_ response.

> *Warning - always fetch metadata!*
>
> Questions should not be cached or stored by the API caller, they can change often and in order to create a compliant submittable filing, from an API embedded solution, you must call the `/metadata` endpoint every time, to get the most up-to-date questions to present to the user.
>
> Metadata for the same country and the same return category, can be different if the period changes or if the requested filing format changes.

#### POST /reports/filing
``` POST /v0/filer/vat/filings/events/companies/:id/filings/:id/periods/:id/reports/filing ```

> *Warning - synchronous request & response!*
>
> In order to provide the filing with the answers provided this journey is implemented with a synchronous post request with the filing returned as the response. 
>
> This typically takes less than a few seconds to return, but your implementation should consider any timeouts your API client might default to, and make sure it maintains this request for long enough to receive the filing. 

**Request body**
```json
    "format": "xml",
    "questions": [
        {
            "answer": "Regular submission",
            "id": "indicate-the-type-of-return",
            "sectionIndex": 0,
            "orderIndex": 0,
            "required": false,
            "label": "Indicate the type of return",
            "type": "select",
            "options": [
                "Regular submission",
                "Correction"
            ],
        }
    ]
```

**Response body**

Depending on the format of the filing, the response may be `application/xml`, `application/json`, `text/csv`, `text/plain` so the API client should check the content-type returned and then save the response in an appropriately named and encoded file.