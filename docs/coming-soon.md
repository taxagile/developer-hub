<img src="../docs/Tax_Agile_Logo_White_on_Purple.png" width="80">

[Home](../README.md) \| [Getting started](getting-started.md)  \|  [Postman](postman.md) \| [Swagger](swagger/index.html) \| [Change log](changelog.md) \| [Coming soon](coming-soon.md)

# Coming soon
## Q1/2026
* We intend to issue the `v1` for **Companies** with full documentation in Swagger early in the quarter
* The VAT Filer API will have more functionality added to the Developer Preview as we round out the capabilities to allow a better embedded filing experience. This is dependant on early adoption feedback so we aren't sure when the Filer endpoints will mature to `v1` but it will be soon.


# Developer Previews
## VAT transactions
We have included endpoints under the `datamanager/vat/transactions` route in the "Developer Preview" of the Postman sample collection. 

## Companies 
Companies API is included from the v1.3.6 Postman sample collection under "Developer Previews" and includes POST, PUT, GET and DELETE operations. 

We plan to convert this preview into an official a documented `v1` resource in Q1/2026.

### VAT Filer
We are continuing our implentation of VAT Filer using the API, and at the very start of 2026 we released some of the VAT Filer endpoints into Developer Preview marked with the `v0` version. 

The journeys included are: 
* Get a list of filings available
* Get a list of filing events based on company setup
* Get an HTML visual preview of the period including the data
* Get the additional questions the filing requires to be answered 
* Get the downloadable fileable version of the filing, providing the answers to the filing questions

