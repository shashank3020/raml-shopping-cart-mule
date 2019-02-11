Shopping Cart API

#API Security:
	* Basic JWT Token Validation is Used.
	* Every Endpoint  will have JWT Authorization Token
	* Token can be generated from jwt.io and using aud=splunk and sub=shoppingcart and iss=architect, rest of the parameters do not matter at this point.

	* Example Token:
		eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJzaG9wcGluZ2NhcnQiLCJhdWQiOiJzcGx1bmsiLCJpc3MiOiJhcmNoaXRlY3QiLCJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1MTYyMzkwMjJ9.aTdXQvnO99sVZFnCRYXHLGpxjJU9rJwsroarcf4sFn8

##Run It:
Best way is to launch this application in Studio, use Console to hit the endpoint.

#Create a Cart:
If you need to use Postman
url : http://127.0.0.1:8081/api/shoppingCarts/
method : POST
Header Authorization : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJzaG9wcGluZ2NhcnQiLCJhdWQiOiJzcGx1bmsiLCJpc3MiOiJhcmNoaXRlY3QiLCJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1MTYyMzkwMjJ9.aTdXQvnO99sVZFnCRYXHLGpxjJU9rJwsroarcf4sFn8
body : 
          [
            {
              "customerId"  : "cus0001",
                "items" : [
                  {
                    "itemId"          : "SI0001",
                    "itemName"        : "Splunk Light",
                    "itemDescription" : "The comprehensive solution for small IT environments looking to automate log search and analysis.",
                    "quantity"        : 2
                  },
                  {
                    "itemId"          : "SI0002",
                    "itemName"        : "Splunk Cloud",
                    "itemDescription" : "Deploy Splunk securely, reliably and scalably as a service. No infrastructure required.",
                    "quantity"        : 2
                  }
                ]
              }
          ]
          
Update Cart:
url : http://127.0.0.1:8081/api/shoppingCarts/{shoppingCartId}
method : PUT
Header Authorization : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJzaG9wcGluZ2NhcnQiLCJhdWQiOiJzcGx1bmsiLCJpc3MiOiJhcmNoaXRlY3QiLCJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1MTYyMzkwMjJ9.aTdXQvnO99sVZFnCRYXHLGpxjJU9rJwsroarcf4sFn8
body : 
{
      "customerId"  : "cus0001",
        "items" : [
          {
            "itemId"          : "SI0001",
            "itemName"        : "Splunk Light",
            "itemDescription" : "The comprehensive solution for small IT environments looking to automate log search and analysis.",
            "quantity"        : 2
          }
        ]
      }

Get Cart:
url : http://127.0.0.1:8081/api/shoppingCarts/{shoppingCartId}
method : GET
Header Authorization : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJzaG9wcGluZ2NhcnQiLCJhdWQiOiJzcGx1bmsiLCJpc3MiOiJhcmNoaXRlY3QiLCJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1MTYyMzkwMjJ9.aTdXQvnO99sVZFnCRYXHLGpxjJU9rJwsroarcf4sFn8

## Architectural StandPoints
	* RAML Design is basically to show how things can be designed in modular way
	* Security Scheme is not used, instead we going with Basic JWT Token Authentication, alternate could be Basic Authentication, ClientId/ClientSecret if host on Anypoint, OAuth
	* Ideally in an Org, we should not be looking at RAML from Project perspective, but its a Org wide asset and needs to be reused.
	* Only Specific set of People should be designing RAML, else we can land in situation that, even with all Modularity we are still duplicating, as at times coding is better than Searching what others has written
	* Mule Application is very basic, but it tells how flows should be designed, small but doing what it needs to.
	* Exception Handling, we were not able to cover a lot of Scenarios but a gist of how Exception handling can work.


          
          