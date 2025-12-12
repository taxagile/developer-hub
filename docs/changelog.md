<img src="../docs/Tax_Agile_Logo_White_on_Purple.png" width="80">

[Home](../README.md) \| [Getting started](getting-started.md)  \|  [Postman](postman.md) \| [Swagger](swagger/index.html) \| [Change log](changelog.md) \| [Coming soon](coming-soon.md)

# Change Log
### v1.3.8 - 2025-12-12
* The "VAT Determination - Response" object schema was updated to include additional attributes which affects:
  * Changed ```POST /v1/determination/vat/transactions```
  * Changed ```GET /v1/determination/vat/transactions```
  * Changed ```GET /v1/determination/vat/transactions/{id}```
  * Changed ```GET /v1/auditor/vat/audits/{id}/results```
* Updated [Swagger](swagger/index.html)
* Sample [Postman collection v1.3.6](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.6.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.8)

### v1.3.7 - 2025-12-05
* TLS minimum version of 1.2 is now enforced, with weaker CBC ciphers not offered.
* We added a [Coming soon](coming-soon.md) page to this Developer Hub to give you some early visibility of API changes in development.
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.7)

### v1.3.6 - 2025-11-29
* Introduced the Companies resource within the 'Developer Previews' folder of the Sample Postman collection. These are previews and are declared with the `v0` versioning so may change without notice. We would welcome feedback on any issues found on these endpoints, so we can move to `v1` published endpoints in early 2026.
  * Preview ``` POST /v0/companies ```
  * Preview ``` GET /v0/companies ```
  * Preview ``` GET /v0/companies/{id} ```
  * Preview ``` PUT /v0/companies/{id} ```
  * Preview ``` DELETE /v0/companies/{id} ```
* Sample [Postman collection v1.3.6](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.6.postman_collection.json)

> **TLS minimum version 1.2** 
> 
> With this release, we planned to disable earlier TLS versions and disable the CBC ciphers. However, due to this release being made on 29/Nov between Black Friday and Cyber Monday; we postponed this change, until our next release. 
>
> Please ensure your API client is supporting TLS 1.2.


### v1.3.5 - 2025-05-09
* Changed ``` GET /v1/determination/vat/transactions/:id ``` to return a more specific value in the field `source`. Previously it would state `api` but not it states `calculator-api`.
* Sample [Postman collection v1.3.5](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.5.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.5)

### v1.3.4 - 2025-02-09
* Changed ``` POST /v1/datamanager/vat/uploads ``` to add more validation multpart/form-data use-case, returning more detailed error codes/messages
* Sample (same as v1.3.3 no changes) [Postman collection v1.3.3](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.3.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.4)

### v1.3.3 - 2024-12-14
* Changed ``` POST /v1/datamanager/vat/uploads ``` to support a data mapping being used on a JSON body payload
* Sample [Postman collection v1.3.3](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.3.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.3)

### v1.3.2 - 2024-11-11
* Updated the VAT Data Model schema in swagger docs
  * Previously we were not correctly representing the data type `number` in the schema documentation.
  * We have corrected that, so now the schema matches the examples provided in the Postman collection.
* Sample (same as v1.3.0 no changes) [Postman collection v1.3.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.0.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.2)

### v1.3.1 - 2024-09-30
* Moved the API infrastructure to be accessed via a load balancer
* Added staging-api.taxagile.io endpoint to swagger docs
* Removed test-api.taxagile.io from documentation (deprecated)
* Updated VAT Data model to include new item types
  * Admission to virtual events
  * Electric vehicle charging
* Changed ``` POST /v1/datamanager/vat/uploads ``` and ``` POST /v1/auditor/vat/audits ``` to validate the request body dates are sent in YYYY-MM-DD format. If not, a 400 will be returned.
* Updated Swagger.json as it had some minor typos in the v1.3.0 release.
* Sample (same as v1.3.0 no changes) [Postman collection v1.3.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.0.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.1)

### v1.3.0 - 2024-08-09
* Published ``` POST /v1/datamanager/vat/uploads ```
* Published ``` GET /v1/datamanager/vat/uploads ```
* Published ``` GET /v1/datamanager/vat/uploads/{id} ```
* Published ``` DELETE /v1/datamanager/vat/uploads/{id} ```
* Changed ``` POST /v1/auditor/vat/audits ```
* Changed ``` GET /v1/auditor/vat/audits ```
* Changed ``` GET /v1/auditor/vat/audits/{id} ```
* Changed ``` GET /v1/auditor/vat/audits/{id}/results ```
* Changed ``` DELETE /v1/auditor/vat/audits/{id} ```
* Sample [Postman collection v1.3.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.0.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.3.0)

### v1.2.5 - 2024-05-22
* Updated ``` POST /v1/determination/vat/transactions ``` 
  * Added a query parameter ``` taxCodeScheme ``` which can be used with ``` useTaxCodes ``` parameter to specify whether the taxCode in the response body is from Tax Codes setup in your account, or returning a known scheme (e.g. Avalara).
* Sample [Postman collection v1.2.5](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.5.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.2.5)

### v1.2.4 - 2024-05-03
* Added support for the Avalara iVAT Reporting XML as an input format for VAT Filer
  *  Updated ``` POST /v1/auditor/vat/audits ```
* Sample [Postman collection v1.2.4](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.4.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.2.4)

### v1.2.3 - 2024-02-20
* Updated VAT Data model to add 4 new fields:
  * date.originalDocDate
  * document.originalDocNumber
  * item.originalValue
  * item.originalVatAmountToCheck
* These fields are available in the body requests of: 
  * ``` POST /v1/determination/vat/transactions ```
  * ``` POST /v1/auditor/vat/audits ```
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.2.3)

### v1.2.2 - 2023-11-28
* Updated ``` GET /v1/auditor/vat/audits/{id}/results```
* Sample [Postman collection v1.2.2](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.2.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.2.2)

### v1.2.1 - 2023-11-10
* Updated ``` POST /v1/determination/vat/transactions```
* Sample [Postman collection v1.2.1](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.1.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.2.1)

### v1.2.0 - 2023-09-15
* Updated ``` POST /v1/determination/vat/transactions```
* Sample [Postman collection v1.2.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.0.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.2.0)

### v1.1.2 - VAT Auditor - GA - v1 - 2023-07-28
* Published ``` GET /v1/auditor/vat/audits/ ```
* Published ``` GET /v1/auditor/vat/audits/{id} ```
* Published ``` GET /v1/auditor/vat/audits/{id}/results ```
* Sample [Postman collection v1.1.2](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.2.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.1.2)

### v1.1.1 - 2023-06-02
* Published ``` GET /v0/auditor/vat/audits/{id}/results ```
* Sample [Postman collection v1.1.1](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.1.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.1.1)

### v1.1.0 - VAT Auditor - Preview - v0 - 2023-04-28
* Published ``` POST /v1/auditor/vat/audits ```
* Published ``` GET /v0/auditor/vat/audits ```
* Published ``` GET /v0/auditor/vat/audits/{id} ```
* Published ``` DELETE /v1/auditor/vat/audits/{id} ```
* Published ``` GET /v1/operations/{id} ```
* Sample [Postman collection v1.1.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.0.postman_collection.json)
* Release note [Release](https://github.com/taxagile/developer-hub/releases/tag/v1.1.0)

### v1.0.2 - 2023-01-06
* Added ```isExternalTransit = false``` to sample body
* Updated the response body of the transaction detail request
```GET /v1/determination/vat/transactions/{id}?detail=true```
* Sample [Postman collection v1.0.2](Tax%20Agile%20-%20sample%20collection%20-%20v1.0.2.postman_collection.json)

### v1.0.1 - VAT Determination - 2022-06-29
* Published ```GET /v1/determination/vat/transactions```
* Published ```GET /v1/determination/vat/transactions/{id}```
* Sample [Postman collection v1.0.1](Tax%20Agile%20-%20sample%20collection%20-%20v1.0.1.postman_collection.json)

### v1.0.0 - VAT Determination - GA - v1 - 2022-06-28
* Published ```POST /v1/determination/vat/transactions```
