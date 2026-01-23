<img src="../docs/Tax_Agile_Logo_White_on_Purple.png" width="80">

[Home](../README.md) \| [Getting started](getting-started.md)  \|  [Postman](postman.md) \| [Swagger](swagger/index.html) \| [Change log](changelog.md) \| [Coming soon](coming-soon.md) | [Tax Agile API - new!](../redoc-static.html)

# Getting started
The Tax Agile API is a RESTful implementation closely following [Microsoft API design guidance](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design) 
which means we have methods (actions) that are performed against resources over https; in a stateless way.

All requests and responses are in application/json, and we return consistent error objects in the form:
```json
{
  "errorCode": "<code>",
  "message": "<text>"
}
```
If more than one error is triggered, we will return the first, instead of returning an array of errors. 

## Documentation
We have provided these documents to help you implement to our API:

| Document                              | What you need it for                                                                                                                                                                                                                                                                                                                                           |
|:--------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Swagger API Doc](swagger/index.html) | This is a standard for developers and it contains all of the options available on the API.                                                                                                                                                                                                                                                                     |
| [Postman Sample](postman.md)          | More interactive and demonstrable the Postman collection shows you real life examples of the requests and responses. <br /><br />You can duplicate and modify to test out your transaction types. <br /><br />Postman also allows you to export requests in other languages (C#, NodeJS, PHP, Ruby) so your developers can see the docs how they like to work. |

## FAQ
<details><summary>Do I send to Production or Staging?</summary>
<p>
<br />
Both environments will function the same, however you will have a different set of credentials for 
the two environments. 
<br />
If you want to make requests that are not saved, you can omit the `commit=true` parameter on the POST /transactions request.
<br />
<table>
<th>Server</th><th>API_ROOT</th>
<tr><td>Production</td><td>https://api.taxagile.io </td></tr>
<tr><td>Staging</td><td>https://staging-api.taxagile.io </td></tr>
</table>
<br />
Note: The Staging environment may be running a new functionality pending deployment to Production!
</p>
</details>

<details><summary>Does my API client need to Authenticate before each request?</summary>
<p>
<br />
No, but you can. The Bearer token is valid for 24hrs; so depending on your integration process flow you may prefer to Authenticate each time you want to make a request. 
<br /><br />
It would be robust if your API client handled the 401 Unauthorized response, by Authenticating again.
<pre>
{
"errorCode": "AU001",
"message": "Unauthorized"
}
</pre>
</p>
</details>

<details><summary>Asynchronous or Synchronous request handling?</summary>
<p>
<br />
The API uses both depending on use-case; when there is a database write this is done via a message bus model. This 
means that you can expect an immediate response once we have written the message to the bus.
<br /><br />
Your calling client you should handle 'eventual consistency'; meaning that if you post a new transaction and immediately try
to fetch it, you may get a 404 Not Found; but a second later it will be found.
</p>
</details>

## See also

- [Swagger document](swagger/index.html)
- [Postman sample collection](postman.md)
- [Filer getting started](filer/filer-overview.md)

