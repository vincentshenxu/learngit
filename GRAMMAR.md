#Grammar
* * *

Each generated Code respect a grammar to define how the Code is randomly generated.

##Grammar Payload

Authorized regex must:
* contain at most 20 variable characters


| Name          | Type          | Attributes     | Description                                                                |
| ------------- | ------------- | -------------- | -------------------------------------------------------------------------- |
| id            | String        | Read-only      | the Id of the Grammar  |
| name          | String        | **Required**   | The name of the Grammar                                                        |
| regex         | String        |                | The regex which the Code need to complied. For example: `[A-Za-z]{8}` allows only 8-bit letters, it cannot begin with "^" or end with "$"  |
| aliases       | [String]      |                | A list of prefixes used to generate aliases |
| used          | Boolean       |                | Indicate whether the grammar has been used |

* * *

##Create a Grammar

`POST /api/grammars`

Create a new Grammar for be used in a Code generation.

###Request
```
POST /api/grammars
Authorization: Bearer {{accessToken}}
Content-Type: application/json

{
  "name":"Chinese Bottle",
  "regex":"[A-Za-z]{8}",
  "aliases": [
    "http://eg.m4g.co/",
    "http://sim.m4g.co/"
  ],
  "used":false
}
```

###Response
```
201 CREATED
Content-Type: application/json

{
  "id":"561a0ce4e4b0f3a92bf36b34",
  "name":"Chinese Bottle",
  "regex":"[A-Za-z]{8}",
  "aliases": [
    "http://eg.m4g.co/",
    "http://sim.m4g.co/"
  ],
  "numberOfPossibleCode": 53459728531456,
  "codeExample": "LHySwNZX"
}
```

The response payload contains the complete Grammar document with the Id of the object just created. 

* * *

##List Grammars

`GET /api/grammars`

Get all the Grammars

###Request
```
GET /api/grammars
Authorization: Bearer {{accessToken}}
Content-Type: application/json
```

###Response
```
200 OK
Content-Type: application/json

[
  {
    "id":"561a0ce4e4b0f3a92bf36b34",
    "name":"Chinese Bottle",
    "regex":"[A-Za-z]{8}",
	"aliases": [
      "http://eg.m4g.co/",
      "http://sim.m4g.co/"
	]
  },
  {
    "id":"561a0ce4e4b0f3a92bf36b35",
    "name":"French Bottle",
    "regex":"[A-Z0-9]{8}"
	"aliases": [
      "http://pwc.m4g.co/"
	]
  }
]
```

* * *

##Read a single Grammar

`GET /api/grammars/:grammarId`

Get an unique Grammar by grammarId

###Request
```
GET /api/grammars/:grammarId
Authorization: Bearer {{accessToken}}
Content-Type: application/json
```

###Response
```
200 OK
Content-Type: application/json

{
  "id":"561a0ce4e4b0f3a92bf36b34",
  "name":"Chinese Bottle",
  "regex":"[A-Za-z]{8}",
  "aliases": [
    "http://eg.m4g.co/",
    "http://sim.m4g.co/"
  ]
}
```

* * *

##Update a Grammar

`PUT /api/grammars`

Update an existing Grammar.

###Request
```
PUT /api/grammars
Authorization: Bearer {{accessToken}}
Content-Type: application/json

{
  "id":"561a0ce4e4b0f3a92bf36b34",
  "name":"Chinese Cap",
  "regex":"[A-Za-z]{8}",
  "aliases": [
    "http://eg.m4g.co/",
    "http://sim.m4g.co/"
  ]
}
```

###Response
```
200 OK
Content-Type: application/json

{
  "id":"561a0ce4e4b0f3a92bf36b34",
  "name":"Chinese Cap",
  "regex":"[A-Za-z]{8}",
  "aliases": [
    "http://eg.m4g.co/",
    "http://sim.m4g.co/"
  ],
  "numberOfPossibleCode": "53459728531456",
  "codeExample": "vXnKaGgE"
}
```

* * *

##Delete a Grammar

`DELETE /api/grammars/:grammarId`

Delete a Grammar by grammarId.

###Request
```
DELETE /api/grammars/:grammarId
Authorization: Bearer {{accessToken}}
Content-Type: application/json
```

###Response
```
200 OK
Content-Type: application/json

```
