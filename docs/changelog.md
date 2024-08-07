# Change Log
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
