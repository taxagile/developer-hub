<img src="../docs/Tax_Agile_Logo_White_on_Purple.png" width="80">

[Home](../README.md) \| [Getting started](getting-started.md)  \|  [Postman](postman.md) \| [Swagger](swagger/index.html) \| [Change log](changelog.md) \| [Coming soon](coming-soon.md)

# Coming soon
## Q4/2025
### VAT Filer - v0 preview
We are continuing our implentation of VAT Filer using the API, this has so far included some Alpha endpoints being used internally, which you may have seen demonstrated. As we complete this work, we will be moving the first endpoints into Developer Preview in late Q4/2025 or early Q1/2026 as `v0` endpoints which may still undergo signficant changes. 

The journeys in the first delivery will include: 
* Get a list of filings which the platform provides
* Get a list of filings setup in Companies
* Get details of the values which can be provided to call specific filings, for example their view languages, or downloadable formats
* Get an HTML visual preview of the period including the data
* Get the additional questions the filing requires to be answered 
* Get the downloadable fileable version of the filing, providing the answers to the filing questions

If you are interested in integrating to this API and would like to be kept informed of the status of this work, please alert us by submitting a ticket.

# Developer Previews
## VAT transactions
We have included endpoints under the `datamanager/vat/transactions` route in the "Developer Preview" of the Postman sample collection. 

## Companies 
Companies API is included from the v1.3.6 Postman sample collection under "Developer Previews" and includes POST, PUT, GET and DELETE operations. 

We plan to convert this preview into an official a documented `v1` resource in Q1/2026.

