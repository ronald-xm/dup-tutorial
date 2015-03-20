paThis doc describes the API provided by the topology server side.

## CI operations

### Get CI detail

**GET** ```/ci/:id```

Get CI detail for the specified ciNo. 

*Parameter:*

id: string as the ciNo of the CI

*Success response:*

An object of response for the request, example as below. Returned data resides in content field as string.

```json
{
	"status": "OK",
	"content": "{
		\"id\": \"CI_20150319000001\",
		\"ciTpNm\": \"NET\",
		\"funcTpNm\": \"\",
		\"hostNm\": \"localhost\",
		\"idcNm\": \"CD\",
		\"ipAddr\": \"127.0.0.1\",
		\"ciAdminNm1\": \"Admin1\",
		\"ciAdminNm2\": \"\",
		\"ciStatusNm\": \"Y\",
		\"manufactNm\": \"\",
		\"modelNm\": \"\",
		\"ownerNm\": \"\",
		\"lastModTime\": \"\"
	}"
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

### Create virtual CI

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

### Update virtual CI

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

### Delete virtual CI

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

### Search CIs

**POST** ```/ci/search?pageSize=:pageSize&pageNum=:pageNum```

Search for list of CIs with the specified condistions.

*Request body:* 

A CI object, example as below

```json
{
	"id": "CI_20150319000001",
	"ciTpNm": "NET",
	"hostNm": "localhost",
	"ipAddr": "127.0.0.1"
}
```

**NOTE:** Each of the property in the above object is optional, and for ciTpNm the valid values are: **NET**, **SVR**, and **VNODE**.

*Parameter:*

pageSize: an integer stands for page size, default to 10.

pageNum: an integer stands for requested page number, default to 1.

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

### Search virtual CIs

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

## Link operations

### Create virtual link

**POST** ```/link```

Create a new virtual link for specified CIs.

*Request body:*

And object represents a link, example as below

```json
{
	"srcCI": {
		"id": "CI_20070119000875"		
	},
	"srcIfIdx": "10",
	"srcIfDesc": "port 1",
	"dstCI": {
		"id": "CI_20150319000001"
	},
	"dstIfIdx": "12",
	"dstIfDesc": "conn port 2",
	"relStatNm": "Y",
	"relSize": "100",
	"relDesc": "test link"
}
```

**NOTE:** 

id for srcCI and dstCI are mandatory, and also srcIfIdx and dstIfIdx. The other fields are optional. 

Either of the source CI or destination CI needs to be virutal, otherwise will report error.

*Success response:*

An object, with status and the id for the newly create link, example as below

```json
{
  "status": "OK",
  "content": "21897"
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

### Update virtual link

**PUT** ```/link/:id```

Update the virtual link of the specified id.

*Request body:*

```json
{
	"srcCI": {
		"id": "CI_20070119000875"		
	},
	"srcIfIdx": "10",
	"srcIfDesc": "test port 2",
	"dstCI": {
		"id": "CI_20150319000003"
	},
	"dstIfIdx": "15",
	"dstIfDesc": "conn port 3",
	"relStatNm": "Y",
	"relSize": "40",
	"relDesc": "test link"
}
```

*Parameter:*

id: id of the link to be updated.

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

### Remove virtual link

**DELETE** ```/link/:id```

Delete virtual link with the specified id.

*Parameter:*

id: id of the virtual link to be deleted.

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

### Get link detail

**GET** ```/link/:id```

Get detail of a link with the specified id.

*Parameter:*

id: id of the virtual link to be deleted.

*Success response:*

```json
{
	"status": "OK",
	"content": "{
		\"srcCI\": {
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
		\"srcIfIdx\": \"10\",
		\"srcIfDesc\": \"port 1\",
		\"dstCI\": {
      		\"ciAdminNm1\": \"admin\",
      		\"ciStatusNm\": \"Y\",
      		\"ciTpNm\": \"VNODE\",
      		\"funcTpNm\": \"OOB\",
      		\"hostNm\": \"oob.e08-r04-3.summit 48si.krlgg\",
      		\"id\": \"CI_20130119000876\",
      		\"idcNm\": \"CD\",
      		\"ipAddr\": \"\",
      		\"lastModTime\": 1426825239000,
      		\"modelNm\": \"SUMMIT 48SI\"
    	},
		\"dstIfIdx\": \"12\",
		\"dstIfDesc\": \"conn port 2\",
		\"relTpNm\": \"NET-VNODE\",
		\"relStatNm\": \"Y\",
		\"relSize\": \"100\",
		\"relDesc\": \"test link\"
	}"
}
```

**NOTE:**

relTpNm value can be "NET-NET", "NET-SVR" or "NET-VNODE".

*Error response:*

```json
{
	"status": "ERR",
	"error": "entry.not.found"
}
```

----------

### Get links for node

**GET** ```/link/ci/:id?pageSize=:pageSize&pageNum=:pageNum```

Get the list of links that use the specified CI as the source.

*Parameter:*

id: id of a CI.

pageSize: an integer stands for page size, default to 10.

pageNum: an integer stands for requested page number, default to 1. 

*Success response:*

```json
{
	"status": "OK",
	"content": "[{
		\"srcCI\": {
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
		\"srcIfIdx\": \"10\",
		\"srcIfDesc\": \"port 1\",
		\"dstCI\": {
      		\"ciAdminNm1\": \"admin\",
      		\"ciStatusNm\": \"Y\",
      		\"ciTpNm\": \"NET\",
      		\"funcTpNm\": \"OOB\",
      		\"hostNm\": \"oob.e08-r04-3.summit 48si.krlgg\",
      		\"id\": \"CI_20130119000876\",
      		\"idcNm\": \"CD\",
      		\"ipAddr\": \"\",
      		\"lastModTime\": 1426825239000,
      		\"modelNm\": \"SUMMIT 48SI\"
    	},
		\"dstIfIdx\": \"12\",
		\"dstIfDesc\": \"conn port 2\",
		\"relTpNm\": \"NET-NET\",
		\"relStatNm\": \"Y\",
		\"relSize\": \"100\",
		\"relDesc\": \"test link\"
	}]",
	"pageSize": 1,
  	"pageNum": 2,
  	"total": 236
}
```

**NOTE:**

relTpNm value can be "NET-NET", "NET-SVR" or "NET-VNODE".

*Error response:*

```json
{
	"status": "ERR",
	"error": "internal.error"
}
```

----------

### Get virtual links for node

**GET** ```/link/ci/:id?pageSize=:pageSize&pageNum=:pageNum```

Get the list of virtual links that use the specified CI as the source.

*Parameter:*

id: id of a CI.

pageSize: an integer stands for page size, default to 10.

pageNum: an integer stands for requested page number, default to 1. 

*Success response:*

```json
{
	"status": "OK",
	"content": "[{
		\"srcCI\": {
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
		\"srcIfIdx\": \"10\",
		\"srcIfDesc\": \"port 1\",
		\"dstCI\": {
      		\"ciAdminNm1\": \"admin\",
      		\"ciStatusNm\": \"Y\",
      		\"ciTpNm\": \"VNODE\",
      		\"funcTpNm\": \"OOB\",
      		\"hostNm\": \"oob.e08-r04-3.summit 48si.krlgg\",
      		\"id\": \"CI_20150119000016\",
      		\"idcNm\": \"CD\",
      		\"ipAddr\": \"\",
      		\"lastModTime\": 1426825239000,
      		\"modelNm\": \"SUMMIT 48SI\"
    	},
		\"dstIfIdx\": \"12\",
		\"dstIfDesc\": \"conn port 2\",
		\"relTpNm\": \"NET-VNODE\",
		\"relStatNm\": \"Y\",
		\"relSize\": \"100\",
		\"relDesc\": \"test link\"
	}]",
	"pageSize": 1,
  	"pageNum": 2,
  	"total": 236
}
```

*Error response:*

```json
{
	"status": "ERR",
	"error": "internal.error"
}
```

## Map operations


## Appendix

### Error codes

Below is the list of error code, with code and briefed explaination.

*duplicated.entry*

Can be reported when create new CI or link, if ciNo already exist for a CI, or if source and destination CI already exist for a link.

*ci.not.found*

System is not able to find a CI with the specified id or properties.

*link.not.found*

System is not able to find a link with the specified id or properties.

*operate.non.virtual.not.allowed*

Reported when try to update or delete a non-virtual CI or link.

*internal.error*

Reported when some internal error happens.

*invalid.request*

Server side is receiving invalid request, like some required field is empty, or invalid request format.

