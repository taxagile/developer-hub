<img src="../docs/Tax_Agile_Logo_White_on_Purple.png" width="80">

[Home](../README.md) \| [Getting started](getting-started.md)  \|  [Postman](postman.md) \| [Swagger](swagger/index.html) \| [Change log](changelog.md) \| [Coming soon](coming-soon.md)

# Postman sample collection
The Postman collection is available to help you get started integrating to the Tax Agile API; and is published with
each version of the API; it has example requests that are setup ready to go, all you need to do is plug
in your credentials and send the requests. 

Using the tools built into Postman you can view the requests in different client implementation languages, you can also
duplicate the sample collection and modify the requests to meet your implementation.

## Setup

* [Download the sample collection](./Tax%20Agile%20-%20sample%20collection%20-%20v1.3.6.postman_collection.json) (Right-click on like, and 'Save as...')
* Setup an [Environment](https://learning.postman.com/docs/sending-requests/managing-environments/) and set these three fields...

### API_ROOT
This is the server hosting the API you want to make requests to, possible values are:


| Server     | API_ROOT                      |
|:-----------|:------------------------------|
| Production | https://api.taxagile.io       |
| Staging       | https://staging-api.taxagile.io  |


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


## Postman settings
### Redirects
By default, Postman will follow redirects, but for a logical demonstration of the API, it is preferable to see the response, and then make a new request to the new location.

In the sample collection, we have changed the default setting "Automatically follow redirects" to OFF; on the operations poll request so that you can see the 303 response; before calling the GET Audit summary by ID.

### File Upload
There is the option to use a form-data body, to send an Excel sheet to VAT Auditor, however you must give Postman permission to read the files on your local machine.

This community post may help: [Postman Community](https://community.postman.com/t/cant-select-file-at-form-data-make-sure-that-postman-can-read-files-inside-the-working-directory/16440/2)
