<style>
th{ background-color: #343a98!important; color: #fff!important; }
</style> 

![Tax Agile Logo](docs/Tax-Agile-Short.png)

[Home](https://taxagile.github.io/developer-hub/) \| [Getting started](docs/getting-started.md) \|  [Postman](docs/postman.md) \| [Swagger](docs/swagger/index.html) \| [Change log](docs/changelog.md)

# Developer Hub
The Tax Agile Developer Hub contains resources for developers integrating with Tax Agile. 

It includes [API Swagger OAS3 docs](docs/swagger/index.html), [sample API requests](docs/postman.md) and documentation to [get started](docs/getting-started.md).

The Hub is hosted on GitHub and you can report issues to us using the GitHub Issues functionality.

# Overview of the API
[![Generic badge](https://img.shields.io/badge/Version-v1.0.2-green.svg)]()

In this version of the API you have methods to authenticate and invoke the VAT Determination API.

* API key authentication
  * Credential pair of API key and Account id are used to create a Bearer token
  * The token is valid for 24hrs and is used as the Authentication on subsequent requests
* Send a transaction for VAT Determination
  * Receiving back context rich error messaging if your transaction is missing a field required for the determination to complete
  * Returns an analysis for the transaction
  * Allows for the transaction to be sent and not saved, or sent with a commit flag
* Get a list of transactions saved
  * Paginated results
  * Filter parameters on entry date/time range, document number & VAT code
  * This can be used to collect data from Tax Agile and store in your data warehouse

Jump to:
* [Swagger API docs](https://taxagile.github.io/developer-hub)
* [Postman sample collection](./Tax%20Agile%20-%20sample%20collection%20-%20v1.0.1.postman_collection.json) (right click 'Save As...' to save a local copy)


## Need help?

### Getting Credentials
Get in touch via our website: [vatcalc.com/contact](https://www.vatcalc.com/contact/) to setup a demo and we can provide you with a trial!
