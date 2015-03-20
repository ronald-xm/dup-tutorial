This doc describes the API provided by the topology server side.

## CI related

### Get CI detail

----------

**GET** ```/ci/:id```

Get CI detail for the specified ciNo. 

*Parameter:*

id (Path variable): string as the ciNo of the CI

*Success response:*

An object of response for the request, example as below

```json
{
	"status": "OK",
	"content": {
		"id": "CI_20150319000001",
		"ciTpNm": "NET",
		"funcTpNm": "",
		"hostNm": "localhost",
		"idcNm": "CD",
		"ipAddr": "127.0.0.1",
		"ciAdminNm1": "Admin1",
		"ciAdminNm2": "",
		"ciStatusNm": "Y",
		"manufactNm": "",
		"modelNm": "",
		"ownerNm": "",
		"lastModTime": ""
	}
}
```

*Error response:*

An object of the error, 'error' property represent the error code, example as below

```json
{
	"status": "ERR",
	"error": "node.not.found"
}
```

----------

**POST** ```/ci/search```

Search for list for CIs with the specified condistions.

*Parameter:*

ciObj (Request body): a CI object, example as below
pageSize (Request parameter): an integer stands for page size
pageNum (Request parameter): an integer stands for requested page number 

```json
{
	"id": "CI_20150319000001",
	"ciTpNm": "NET",
	"hostNm": "localhost",
	"ipAddr": "127.0.0.1"
}
```

**NOTE:** Each of the property in the above object is optional, and for ciTpNm the valid values are: **NET**, **SVR**, and **VNODE**.

*Success response:*

An object, example as below

```json
{
  "status": "OK",
  "error": null,
  "content": "[{
      \"ciAdminNm1\": \"admin1\",
      \"ciStatusNm\": \"Y\",
      \"ciTpNm\": \"NET\",
      \"funcTpNm\": \"OOB\",
      \"hostNm\": \"\",
      \"id\": \"CI_20070119000875\",
      \"idcNm\": \"CD\",
      \"ipAddr\": \"\",
      \"lastModTime\": 1426825239000,
      \"modelNm\": \"WS-C2950-24-SMI\"
    },
    {
      \"ciAdminNm1\": \"admin\",
      \"ciStatusNm\": \"Y\",
      \"ciTpNm\": \"NET\",
      \"funcTpNm\": \"OOB\",
      \"hostNm\": \"oob.e08-r04-3.summit 48si.krlgg\",
      \"id\": \"CI_20070119000876\",
      \"idcNm\": \"CD\",
      \"ipAddr\": \"\",
      \"lastModTime\": 1426825239000,
      \"modelNm\": \"SUMMIT 48SI\"
    }
	.
	.
	.
  ]",
  "pageSize": 10,
  "pageNum": 2,
  "total": 17959
}
```

*Error response:*

An object of the error, example as below

```json
{
	"status": "ERR",
	"error": "node.not.found"
}
```

----------

aa

## Relation related


## Map related
