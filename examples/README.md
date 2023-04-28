# Maker-Chcker REST API Docs 

This document conatins API Definitions of the Maker-Checker system.




### Transaction related Endpoint

Endpoints for viewing and manipulating the Transactions that the Authenticated User
has permissions to access.

* `POST /maker-checker/api/transactions` : Create a new transaction
* `PUT /maker-checker/api/transactions/{id}` : Update the amount and description of a transaction, can't be used to update status and creator of this transaction
* `GET /maker-checker/api/transactions/{id}` : Get a specific transaction by id
* `GET /maker-checker/api/transactions` : Get transactions(Pagination), by default return the first 10 transactions, you can adjust the number of returns
* `POST /maker-checker/transactions/{id}/approve` : Approve a transaction
*  `POST /maker-checker/transactions/{id}/reject` : Reject a transaction


# Detailed Explanation

## 1.Create a new Transaction

create a new Transaction if current User has access permissions to it.

**URL** : `/maker-checker/api/transactions`

**Method** : `POST`

**Auth required** : YES (Haven't integrate with Token API yet, so no auth at the moment)

**Permissions required** :

User must have maker privilege (Haven't integrate with Token API yet)


**Data from frontend**: 
```json
{
    "description":"Transfer to another bank",
    "amount": 10030,
    "createdBy": "Amber"
 }
```

### Success Response

**Condition** : If Authorized User has required permissions.

**Code** : `201 Created`

**Content example**

```json
{
        "id": 1,
        "description": "Transfer internationally",
        "amount": 4500.00,
        "status": "PENDING",
        "createdBy": "John",
        "approvedBy": null
 }
```


## 2.Update a Transaction

Update a Transaction if current User has access permissions to it.

**URL** : `/maker-checker/api/transactions/{id}`

**Method** : `PUT`

**Auth required** : YES (Haven't integrate with Token API yet)

**Permissions required** :

User must have maker privilege (Haven't integrate with Token API yet)


**Data  from frontend **: 
```json
{
    "description":"Transfer to international account",
    "amount": 10030.123,
 }
```

### Success Response

**Condition** : If Account exists and Authorized User has required permissions.

**Code** : `200 Ok`

**Content example**

```json
{
        
    "success": true,
    "message": "Successfully updated a transaction"

 }
```



## 3.Get many Transaction(pagination)

Update a Transaction if current User has access permissions to it.By default return the first 10 transactions, you can adjust the number of returns

**URL** : `/maker-checker/api/transactions`

**Method** : `GET`

**Auth required** : YES

**Path Parameter(You can provide,If not provided, the system will use default value ):

* PageNo: default: 0
* PageSize: default: 10
* sortBy:   default "id"


**Permissions required** :

User must have maker privilege(Haven't integrate with Token API yet)


### Success Response

**Condition** : If Account exists and Authorized User has required permissions.

**Code** : `200 Ok`

**Content example**

```json
[
    {
        "id": 1,
        "description": "Transferring domestically",
        "amount": 7000.00,
        "status": "PENDING",
        "createdBy": "John",
        "approvedBy": null
    },
    {
        "id": 2,
        "description": "Transfer to another bank",
        "amount": 10030.00,
        "status": "PENDING",
        "createdBy": "Amber",
        "approvedBy": null
    }
]
```


## 4. Approve a transaction

Approve Transaction if current User has access permissions to it.

**URL** : `/maker-checker/api/transactions/{id}/approve`

**Method** : `Post`

**Auth required** : YES
**Data from frontend**: {
"approvedBy": "shelly"
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
    "message": "The transaction has been approved"
}
```



## 5. Reject a transaction

Reject Transaction if current User has access permissions to it.

**URL** : `/maker-checker/api/transactions/{id}/reject`

**Method** : `Post`

**Auth required** : YES

**Data from frontend**: {

"approvedBy": "shelly"
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
    "message": "The transaction has been rejected"
}
```

