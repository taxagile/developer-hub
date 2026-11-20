# Tax Agile - Developer Hub
The Tax Agile Developer Hub contains resources for developers integrating with Tax Agile via RESTful web services. 

It includes [API OAS3 docs](redoc-static.html), [sample API requests](docs/postman.md), and documentation to [get started](docs/getting-started.md).


# Overview of the API
[![Version](https://img.shields.io/badge/Version-v1.4.9-green.svg)](docs/changelog.md) [![API docs](https://img.shields.io/badge/API_docs-OpenAPI_3-blue.svg?logo=openapiinitiative)](redoc-static.html) [![Data model](https://img.shields.io/badge/Data_model-JSON_schema-purple.svg?logo=json)](docs/oas/schemas/vatDataModelSchema.json)

## Authentication

* API key authentication
  * Credential pair of API key and Account id are used to create a Bearer token
  * The token is valid for 24hrs and is used as the Authentication on subsequent requests

## Data manager

* Introduced in v1.3.0 of the API - data manager route handles uploads of data

## VAT Determination

* Send a transaction for VAT Determination
  * Receiving back context rich error messaging if your transaction is missing a field required for the determination to complete
  * Returns an analysis for the transaction
  * Allows for the transaction to be sent and not saved, or sent with a commit flag
  * Can use tax codes setup in the application to include an ERP tax code in the response, with the useTaxCodes flag
* Get a list of transactions saved
  * Paginated results
  * Filter parameters on entry date/time range, document number & VAT code
  * This can be used to collect data from Tax Agile and store in your data warehouse

## VAT Auditor
* Get a list of audits from uploads on the system
* Fetch summary details of a specific audit by upload id
* Fetch audit results by upload id

## VAT Filer
* New to VAT Filer? Start with the [VAT Filer overview](docs/filer/filer-overview.md), which walks through the API calls in order and how they depend on each other
* List VAT Filer capabilites, all filings available on the platform, filter by countryCode and type
* List Filing Events based on date range 
* Fetch visual view of the filing for the user review
* Fetch the electronic filing having answered statutory questions
* Stable preview in Q1/2026 moving to `v1` in Q2/2026

## Companies
* Create, read, update and delete company resources
* Previewed in Nov '25, published as `v0` Jan '26 - stable and ready to use. Moving to `v1` in Q1/2026

## Jump to:
* [API OAS3 docs](redoc-static.html)
* [Postman sample collection](docs/Tax%20Agile%20-%20sample%20collection%20-%20v1.4.8.postman_collection.json) (right click 'Save As...' to save a local copy)
* [VAT Filer overview](docs/filer/filer-overview.md)


## Need help?

### Getting Credentials
Get in touch via our website: [vatcalc.com/contact](https://www.vatcalc.com/contact/) to setup a demo and we can provide you with a trial!

### FAQ
* **Samples**: If you are having any trouble building a request from the OAS documentation, first find the sample for that endpoint in the Postman collection as it contains working payloads, which might help you identify the issue. 
* **Boolean data type**: Provide a boolean `true` or `false`, not a string `"true"` or `"false"`
* **Numbers**: Financial values are represented in JSON as number types, for example `100.00` rather than `"100.00"`


### Contact Support
Create a ticket in our [online service desk](https://vatcalc.freshdesk.com/support/home)