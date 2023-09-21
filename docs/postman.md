<style>
th{ background-color: #343a98!important; color: #fff!important; }
</style> 

![Tax Agile Logo](Tax-Agile-Short.png)

[Home](../README.md) \| [Getting started](getting-started.md) \|  [Postman](postman.md) \| [Swagger](../docs/swagger/index.html) \| [Change log](changelog.md)

# Postman sample collection
The Postman collection is available to help you get started integrating to the Tax Agile API; and is published with
each version of the API; it has example requests that are setup ready to go, all you need to do is plug
in your credentials and send the requests. 

Using the tools built into Postman you can view the requests in different client implementation languages, you can also
duplicate the sample collection and modify the requests to meet your implementation.

## Setup

* [Download the sample collection](./Tax%20Agile%20-%20sample%20collection%20-%20v1.2.0.postman_collection.json)
* Setup an [Environment](https://learning.postman.com/docs/sending-requests/managing-environments/) and set these three fields...

### API_ROOT
This is the server hosting the API you want to make requests to, possible values are:


| Server     | API_ROOT                      |
|:-----------|:------------------------------|
| Production | https://api.taxagile.io       |
| Test       | https://test-api.taxagile.io  |


### ACCOUNT_ID
This is your Tax Agile tenant on our platform, so this is not a username, but instead a identifier of your account as a whole.

We will provide you your Account Id and API key when you start to implement to our API.

_Note: these credentials will be provisioned against a server, so you must use Production credentials with the Production API_ROOT._

### API_KEY
This is a uuid string which will be provided by us when you start to implement to our API.

## Demo requests
In the collection we have included the use-cases which match what our customers use; but there may be options
available on the API which are not demonstrated in the collection, please check our [Swagger](../docs/swagger/index.html) 
for all the available options.

There is a logical order to these requests, by first doing an Auth, the Bearer token is automatically 
used on the following requests. 

| Name | Functionality                                                                       |
| :--- |:------------------------------------------------------------------------------------|
| POST Auth | 	Takes `ACCOUNT_ID` and `API_KEY` environment variables and creates a new Bearer token. |
| POST VAT Determination - ICS | Makes a VAT Determination which is not committed (saved).                           |
| POST VAT Determination - local supply | Makes a VAT Determination which is not committed (saved).                           |
| POST VAT Determination with commit | Makes a VAT Determination with the `commit=true` parameter so save the transaction.   |
| GET VAT Determination by ID | Returns a summary of the request sent and response given for the transaction; using the uuid returned on the commited determination as the ID.                                                                                    |
| GET VAT Determination for date range |     	Queries the commited (saved) transactions and returns a paged result set. The example shows a date/time range filter, but other filter options are set on the request and can be enabled.                                                                                |
| POST Create Audit with json | Submits transaction data to create an Audit. Returns an operation id to poll |
| POST Create Audit - Excel (form-data) | Demonstrates the file upload usage |
| GET Poll operations endpoint | Poll for a completed status |
| GET Audit summary by ID | Using the audit resource id, fetch a summary of the audit |
| GET Audit results by ID | Using the audit resource id, fetch the detail results of the audit with paged responses |
| GET Audits - list latest 100 | List of latest 100 audits | 
| DELETE Audit by ID | Remove an audit from the system |


## Postman settings
### Redirects
By default, Postman will follow redirects, but for a logical demonstration of the API, it is preferable to see the response, and then make a new request to the new location.

In the sample collection, we have changed the default setting "Automatically follow redirects" to OFF; on the operations poll request so that you can see the 303 response; before calling the GET Audit summary by ID.

### File Upload
There is the option to use a form-data body, to send an Excel sheet to VAT Auditor, however you must give Postman permission to read the files on your local machine.

This community post may help: [Postman Community](https://community.postman.com/t/cant-select-file-at-form-data-make-sure-that-postman-can-read-files-inside-the-working-directory/16440/2)
