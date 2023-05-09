# Maker-Chcker REST API Docs 

This document conatins API Definitions of the Maker-Checker system.


### Swagger UI

You can access and test api also through Swagger UI:
Once starts the maker-checker backend, enter the following URL in the browser:
* http://localhost:8080/maker-checker/swagger-ui/index.html 



### Request related Endpoint

Endpoints for viewing and manipulating the Requests that the Authenticated User
has permissions to access.

* `POST /maker-checker/api/requests` : Create a new request
* `GET /maker-checker/api/requests/{id}` : Get a specific request by id
* `GET /maker-checker/api/requests` : Get requests(Pagination), by default return the first 10 requests, you can adjust the number of returns
* `PUT /maker-checker/requests/{id}/approve` : Approve a request
*  `PUT /maker-checker/requests/{id}/reject` : Reject a request


# Detailed Explanation

## 1.Create a new request

create a new request if current User has access permissions to it.

**URL** : `/maker-checker/api/requests`

**Method** : `POST`

**Auth required** : YES (Haven't integrate with Token API yet, so no auth at the moment)

**Permissions required** :

User must have maker privilege (Haven't integrate with Token API yet)


**Data from frontend**: 
```json
{
  "userId": 1,
  "priority": "LOW",
  "reviewsRequired": 5,
  "description": "Account management",
  "typeId": 1
}
```

### Success Response

**Condition** : If Authorized User has required permissions.

**Code** : `201 Created`

**Content example**

```json
{
    "success": true,
    "message": "Successfully create a request"
}
```



## 2.Get many Requests(pagination)

Get at least 10 requests if current User has access permissions to it.By default return the first 10 transactions, you can adjust the number of returns

**URL** : `/maker-checker/api/requests`

**Method** : `GET`

**Auth required** : YES

**Path Parameter(You can provide,If not provided, the system will use default value ):

* PageNo: default: 0
* PageSize: default: 10
* sortBy:   default "requestId"


**Permissions required** :

User must have maker privilege(Haven't integrate with Token API yet)


### Success Response

**Condition** : If Account exists and Authorized User has required permissions.

**Code** : `200 Ok`

**Content example**

```json
[
    {
        "requestId": 1,
        "userId": 1,
        "priority": "LOW",
        "createdAt": "2023-05-09T17:57:41.651012",
        "reviewedAt": null,
        "reviewsRequired": 5,
        "reviewsReceived": 0,
        "description": "Account management",
        "requestStatus": "IN_PROGRESS",
        "typeId": 1
    },
    {
        "requestId": 2,
        "userId": 1,
        "priority": "HIGH",
        "createdAt": "2023-05-09T17:58:14.954211",
        "reviewedAt": null,
        "reviewsRequired": 2,
        "reviewsReceived": 0,
        "description": "International transaction",
        "requestStatus": "IN_PROGRESS",
        "typeId": 1
    }
]
```


## 4. Approve a request

Approve a request if current User has access permissions to it.

**URL** : `/maker-checker/api/requests/{id}/approve`

**Method** : `PUT`

**Auth required** : YES
**Data from frontend**: 
{
  "reviewerId": 2,
  "comment": "the transaction looks legit"
  
}



**Permissions required** :

User must have checker privilege(Haven't integrate with Token API yet)


### Success Response

**Condition** : If Account exists and Authorized User has required permissions.

**Code** : `200 Ok`

**Content example**

```json
{
    "success": true,
    "message": "Your have reviewed a request"
}
```



## 5. Reject a request

Reject a request if current User has access permissions to it.

**URL** : `/maker-checker/api/requests/{id}/reject`

**Method** : `PUT`

**Auth required** : YES

**Data from frontend**: 
{
  "reviewerId": 3,
  "comment": "the transaction is dodge"
  
}


**Permissions required** :

User must have checker privilege(Haven't integrate with Token API yet)


### Success Response

**Condition** : If Account exists and Authorized User has required permissions.

**Code** : `200 Ok`

**Content example**

```json
{
    "success": true,
    "message": "Your have reviewed a request"
}
```

