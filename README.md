This doc describes the API provided by the topology server side.

## CI related

### Get CI detail

**GET** ```/:id```

Get CI detail for the specified ciNo. 

*Parameter:*

id: string, ciNo of the CI

*Success:*

response: object, response for the request

```json
{
	"status": "OK",
	"content": {
		"id": "CI20150319000001",
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



## Relation related


## Map related
