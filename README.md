This doc describes the API provided by the topology server side.

## CI operations

### Get CI detail

----------

**GET** ```/ci/:id```

Get CI detail for the specified ciNo. 

*Parameter:*

id: string as the ciNo of the CI

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

An object of the error, 'error' property represent the error code, example as below. For detail of the error code, please consult the appendix.

```json
{
	"status": "ERR",
	"error": "node.not.found"
}
```

----------

**POST** ```/ci/:id```

Create new virutal CI.

*Request body:* 

A CI object, example as below

```json
{
	"id": "CI_20150319000001",
	"hostNm": "localhost",
	"ipAddr": "127.0.0.1",
	"funcTpNm": "",
	"idcNm": "CD",
	"ciAdminNm1": "admin1",
	"ciAdminNm2": "admin2",
	"ciStatusNm": "Y",
	"manufactNm": "cisco",
	"modelNm": "S1",
	"ownerNm": "",
	"lastModeTime": ""
}
```

*Parameter:*

id: string as the ciNo of the CI

*Success response:*

```json
{
	"status": "OK"
}
```

*Error response:*

```json
{
	"status": "ERR",
	"error": "duplicated.entry"
}
```

----------

**PUT** ```/ci/:id```

Update a virtual CI.

*Request body:* 

A CI object, example as below

```json
{
	"id": "CI_20150319000001",
	"hostNm": "localhost",
	"ipAddr": "127.0.0.1",
	"funcTpNm": "",
	"idcNm": "CD",
	"ciAdminNm1": "admin1",
	"ciAdminNm2": "admin2",
	"ciStatusNm": "Y",
	"manufactNm": "cisco",
	"modelNm": "S1",
	"ownerNm": "",
	"lastModeTime": ""
}
```

*Parameter:*

id: string as the ciNo of the CI

*Success response:*

```json
{
	"status": "OK"
}
```

*Error response:*

```json
{
	"status": "ERR",
	"error": "internal.error"
}
```

----------

**DELETE** ```/ci/:id```

Delete a virtual CI.

*Parameter:*

id: string as the ciNo of the CI

*Success response:*

```json
{
	"status": "OK"
}
```

*Error response:*

```json
{
	"status": "ERR",
	"error": "operate.non.virtual.not.allowed"
}
```

----------

**POST** ```/ci/search?pageSize=:pageSize&pageNum=:pageNum```

Search for list of CIs with the specified condistions.

*Request body:* 

A CI object, example as below

*Parameter:*

pageSize: an integer stands for page size

pageNum: an integer stands for requested page number

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
  ]",
  "pageSize": 2,
  "pageNum": 2,
  "total": 17959
}
```

*Error response:*

An object of the error, example as below

```json
{
	"status": "ERR",
	"error": "internal.error"
}
```

----------

**POST** /ci/search/virtual?pageSize=:pageSize&pageNum=:pageNum

Search for list of virtual CIs with the specified conditions.

*Request body:* 

A CI object, example as below

```json
{
	"id": "CI_20150319000001",
	"hostNm": "localhost",
	"ipAddr": "127.0.0.1"
}
```

*Parameter:*

pageSize: an integer stands for page size

pageNum: an integer stands for requested page number

**NOTE:** Each of the property in the above object is optional.

*Success response:*

An object, example as below

```json
{
  "status": "OK",
  "content": "[{
      \"ciAdminNm1\": \"admin1\",
      \"ciStatusNm\": \"Y\",
      \"ciTpNm\": \"VNODE\",
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
      \"ciTpNm\": \"VNODE\",
      \"funcTpNm\": \"OOB\",
      \"hostNm\": \"oob.e08-r04-3.summit 48si.krlgg\",
      \"id\": \"CI_20070119000876\",
      \"idcNm\": \"CD\",
      \"ipAddr\": \"\",
      \"lastModTime\": 1426825239000,
      \"modelNm\": \"SUMMIT 48SI\"
    }
  ]",
  "pageSize": 2,
  "pageNum": 2,
  "total": 17959
}
```

*Error response:*

An object of the error, example as below

```json
{
	"status": "ERR",
	"error": "internal.error"
}
```

----------



## Relation related


## Map related
