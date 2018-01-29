#Code Name
* * *

A CodeName describes how the code is integrated in real life, its format. Each code has exactly one code name. The scanning of a good could mean different things according to the code name of the code under which it was scanned.

* * *

##Code Name payload

| Name          | Type          | Attributes           | Description                                                                |
| ------------- | ------------- | -------------------- | -------------------------------------------------------------------------- |
| key           | String        | **Required, Unique** | the key of the code name, inputted by user. The key shall be checked again regex `^[a-z][a-z0-9]{1,19}$`. |
| name          | String        | **Required**         | The name of the Code Name: eg "main QR-code" "tamper evident RFID"         |
| type          | [String]      | **Required**         | The list type of Goods the CodeName could be used with. Could be `TAG`, `PACKAGING`, `PRODUCT` - by default it applies to all types of good |
| createdAt     | DateTime      | Read-only            | When the CodeName was created                                              |
| updatedAt     | DateTime      | Read-only            | When the CodeName was last updated                                         |

* * *

##Create a CodeName

`POST /api/code-names`

Create a new CodeName to be used in a Good later.

###Request create a CodeName
```
POST /api/code-names
Authorization: Bearer {{accessToken}}
Content-Type: application/json

{  
  "key":"qr",
  "name":"QR Code",
  "type":["TAG"]
}
```

###Response create a CodeName
```
201 CREATED
Content-Type: application/json

{  
  "id":"561a0ce4e4b0f3a92bf36b34",
  "createdAt":"2016-07-11T07:16:52.503Z",
  "updatedAt":"2016-07-11T07:16:52.503Z",
  "key":"qr",
  "name":"QR Code",
  "type":["TAG"]
}
```

The response payload contains the complete CodeName document with the Id of the object just created. 

* * *

##List CodeNames

`GET /api/code-names`

Get all the CodeNames

###Request list CodeNames
```
GET /api/code-names
Authorization: Bearer {{accessToken}}
Content-Type: application/json
```

###Response list CodeNames
```
200 OK
Content-Type: application/json

[  
  {  
    "id":"561a0ce4e4b0f3a92bf36b34",
    "createdAt":"2016-07-11T07:16:52.503Z",
    "updatedAt":"2016-07-11T07:16:52.503Z",
    "key":"qr",
    "name":"QR CODE",
    "type":["TAG"]
  },
  {  
    "id":"561a0ce4e4b0f3a92bf36b35",
    "createdAt":"2016-08-11T07:16:52.503Z",
    "updatedAt":"2016-08-11T07:16:52.503Z",
    "key":"rfid",
    "name":"RFID Bottle",
    "type":["PRODUCT"]
  }
]
```

* * *

##Read a single CodeName

`GET /api/code-names/{id}`

Get an unique CodeName by CodeNameId

###Request read a single CodeName
```
GET /api/code-names/{id}
Authorization: Bearer {{accessToken}}
Content-Type: application/json
```

###Response read a single CodeName
```
200 OK
Content-Type: application/json

{  
  "id":"561a0ce4e4b0f3a92bf36b34",
  "createdAt":"2016-07-11T07:16:52.503Z",
  "updatedAt":"2016-07-11T07:16:52.503Z",
  "key":"qr",
  "name":"QR Code",
  "type":["TAG"]
}
```

* * *

##Update a CodeName

`PUT /api/code-names`

Update an existing CodeName. Note that `TYPE` and `PACKINGLEVEL` cannot be updated once some goods of this SKU have been generated.

###Request update a CodeName
```
PUT /api/code-names
Authorization: Bearer {{accessToken}}
Content-Type: application/json

{  
  "id":"561a0ce4e4b0f3a92bf36b34",
  "createdAt":"2016-07-11T07:16:52.503Z",
  "updatedAt":"2016-08-11T07:16:52.503Z",
  "key":"qr",
  "name":"QR Code Bottle",
  "type":["PRODUCT"]
}
```

###Response update a CodeName
```
200 OK
Content-Type: application/json

{  
  "id":"561a0ce4e4b0f3a92bf36b34",
  "createdAt":"2016-07-11T07:16:52.503Z",
  "updatedAt":"2016-08-11T07:16:52.503Z",
  "key":"qr",
  "name":"QR Code Bottle",
  "type":["PRODUCT"]
}
```

* * *

##Delete a CodeName

`DELETE /api/code-names/{id}`

Delete a CodeName by CodeNameId.

###Request delete a CodeName
```
DELETE /api/code-names/{id}
Authorization: Bearer {{accessToken}}
Content-Type: application/json
```

###Response delete a CodeName
```
200 OK
Content-Type: application/json

```
