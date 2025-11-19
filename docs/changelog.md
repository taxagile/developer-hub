# Change Log
### v1.3.6
* Introduced the Companies resource within the 'Developer Previews' folder of the Sample Postman collection. These are previews and are declared with the `v0` versioning so may change without notice. We would welcome feedback on any issues found on these endpoints, so we can move to `v1` published endpoints in early 2026.
  * Preview ``` POST /v0/companies ```
  * Preview ``` GET /v0/companies ```
  * Preview ``` GET /v0/companies/{id} ```
  * Preview ``` PUT /v0/companies/{id} ```
  * Preview ``` DELETE /v0/companies/{id} ```
* Sample [Postman collection v1.3.6](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.6.postman_collection.json)

### v1.3.5
* Changed ``` GET /v1/determination/vat/transactions/:id ``` to return a more specific value in the field `source`. Previously it would state `api` but not it states `calculator-api`.
* Sample [Postman collection v1.3.5](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.5.postman_collection.json)

### v1.3.4
* Changed ``` POST /v1/datamanager/vat/uploads ``` to add more validation multpart/form-data use-case, returning more detailed error codes/messages
* Sample (same as v1.3.3 no changes) [Postman collection v1.3.3](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.3.postman_collection.json)

### v1.3.3
* Changed ``` POST /v1/datamanager/vat/uploads ``` to support a data mapping being used on a JSON body payload
* Sample [Postman collection v1.3.3](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.3.postman_collection.json)

### v1.3.2
* Updated the VAT Data Model schema in swagger docs
  * Previously we were not correctly representing the data type `number` in the schema documentation.
  * We have corrected that, so now the schema matches the examples provided in the Postman collection.
* Sample (same as v1.3.0 no changes) [Postman collection v1.3.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.0.postman_collection.json)

### v1.3.1
* Moved the API infrastructure to be accessed via a load balancer
* Added staging-api.taxagile.io endpoint to swagger docs
* Removed test-api.taxagile.io from documentation (deprecated)
* Updated VAT Data model to include new item types
  * Admission to virtual events
  * Electric vehicle charging
* Changed ``` POST /v1/datamanager/vat/uploads ``` and ``` POST /v1/auditor/vat/audits ``` to validate the request body dates are sent in YYYY-MM-DD format. If not, a 400 will be returned.
* Updated Swagger.json as it had some minor typos in the v1.3.0 release.
* Sample (same as v1.3.0 no changes) [Postman collection v1.3.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.3.0.postman_collection.json)

### v1.3.0
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

### v1.2.5
* Updated ``` POST /v1/determination/vat/transactions ``` 
  * Added a query parameter ``` taxCodeScheme ``` which can be used with ``` useTaxCodes ``` parameter to specify whether the taxCode in the response body is from Tax Codes setup in your account, or returning a known scheme (e.g. Avalara).
* Sample [Postman collection v1.2.5](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.5.postman_collection.json)

### v1.2.4
* Added support for the Avalara iVAT Reporting XML as an input format for VAT Filer
  *  Updated ``` POST /v1/auditor/vat/audits ```
* Sample [Postman collection v1.2.4](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.4.postman_collection.json)

### v1.2.3
* Updated VAT Data model to add 4 new fields:
  * date.originalDocDate
  * document.originalDocNumber
  * item.originalValue
  * item.originalVatAmountToCheck
* These fields are available in the body requests of: 
  * ``` POST /v1/determination/vat/transactions ```
  * ``` POST /v1/auditor/vat/audits ```

### v1.2.2
* Updated ``` GET /v1/auditor/vat/audits/{id}/results```
* Sample [Postman collection v1.2.2](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.2.postman_collection.json)

### v1.2.1
* Updated ``` POST /v1/determination/vat/transactions```
* Sample [Postman collection v1.2.1](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.1.postman_collection.json)

### v1.2.0
* Updated ``` POST /v1/determination/vat/transactions```
* Sample [Postman collection v1.2.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.2.0.postman_collection.json)

### v1.1.2 - VAT Auditor - GA - v1
* Published ``` GET /v1/auditor/vat/audits/ ```
* Published ``` GET /v1/auditor/vat/audits/{id} ```
* Published ``` GET /v1/auditor/vat/audits/{id}/results ```
* Sample [Postman collection v1.1.2](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.2.postman_collection.json)

### v1.1.1
* Published ``` GET /v0/auditor/vat/audits/{id}/results ```
* Sample [Postman collection v1.1.1](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.1.postman_collection.json)

### v1.1.0 - VAT Auditor - Preview - v0
* Published ``` POST /v1/auditor/vat/audits ```
* Published ``` GET /v0/auditor/vat/audits ```
* Published ``` GET /v0/auditor/vat/audits/{id} ```
* Published ``` DELETE /v1/auditor/vat/audits/{id} ```
* Published ``` GET /v1/operations/{id} ```
* Sample [Postman collection v1.1.0](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.0.postman_collection.json)

### v1.0.2
* Added ```isExternalTransit = false``` to sample body
* Updated the response body of the transaction detail request
```GET /v1/determination/vat/transactions/{id}?detail=true```
* Sample [Postman collection v1.0.2](Tax%20Agile%20-%20sample%20collection%20-%20v1.0.2.postman_collection.json)

### v1.0.1 - VAT Determination 
* Published ```GET /v1/determination/vat/transactions```
* Published ```GET /v1/determination/vat/transactions/{id}```
* Sample [Postman collection v1.0.1](Tax%20Agile%20-%20sample%20collection%20-%20v1.0.1.postman_collection.json)

### v1.0.0 - VAT Determination - GA - v1
* Published ```POST /v1/determination/vat/transactions```
