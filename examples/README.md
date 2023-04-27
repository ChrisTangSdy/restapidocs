# Maker-Chcker REST API Docs 

These examples were taken from projects mainly using [Django Rest
Framework](https://github.com/tomchristie/django-rest-framework) and so the
JSON responses are often similar to the way in which DRF makes responses.

Where full URLs are provided in responses they will be rendered as if service
is running on 'http://testserver/'.


### Detailed API document

* Go to the broswer enters `http://localhost:8080/maker-checker/swagger-ui/index.html`


### Transaction related

Endpoints for viewing and manipulating the Transactions that the Authenticated User
has permissions to access.

* [Show Accessible Accounts](accounts/get.md) : `POST /maker-checker/api/transactions`
* [Create Account](accounts/post.md) : `PUT /maker-checker/api/transactions/{id}`
* [Show An Account](accounts/pk/get.md) : `GET /maker-checker/api/transactions/{id}`
* [Update An Account](accounts/pk/put.md) : `GET /maker-checker/api/transactions`
