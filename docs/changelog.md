# Change Log

### v1.1.0 - VAT Auditor
* Published ``` POST /v1/auditor/vat/audits ```
* Published ``` GET /v1/auditor/vat/audits ```
* Published ``` GET /v1/auditor/vat/audits/{id} ```
* Published ``` DELETE /v1/auditor/vat/audits/{id} ```
* Published ``` GET /v1/operations/{id} ```
* Published ``` POST /report?? ```
* Published ``` GET /report?? ```
* Sample [Postman collection](Tax%20Agile%20-%20sample%20collection%20-%20v1.1.0.postman_collection.json)

### v1.0.2
* Added ```isExternalTransit = false``` to sample body
* Updated the response body of the transaction detail request
```GET /v1/determination/vat/transactions/{id}?detail=true```
* Sample [Postman collection](Tax%20Agile%20-%20sample%20collection%20-%20v1.0.2.postman_collection.json)

### v1.0.1 - VAT Determination
* Published ```GET /v1/determination/vat/transactions```
* Published ```GET /v1/determination/vat/transactions/{id}```
* Sample [Postman collection](Tax%20Agile%20-%20sample%20collection%20-%20v1.0.1.postman_collection.json)

### v1.0.0 
* Published ```POST /v1/determination/vat/transactions```
