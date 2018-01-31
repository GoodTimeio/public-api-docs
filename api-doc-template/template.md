# DOC TITLE

* [Sample Get Endpoint](#get-sample_get_endpoint)
* [Sample Post Endpoint](#get-sample_post_endpoint)


---

### `GET` `/sample_get_endpoint`
* Returns a list of ATS applications for a guest.

####  Header
key|value
---|---
`example`| value

#### GET Query
params | required | type | comment
---|---|---|---
maxResults | false | Integer | Max number of results to return. Default is 100
offset | false | Integer | Offset of results. Default is 0
query | false | String | Search query

#### Sample Response
```json
{
  "code": 200,
  "status": "success",
  "result": {}
}
```



---


### `POST` `/sample_post_endpoint`

####  Header
key|value
---|---
`example`| value


#### POST Body
params | required | type | comment
---|---|---|---
id | true | String UUID | ID of the object.

#### Sample Response
```json
{
  "code": 200,
  "status": "success",
  "result": {}
}
```


---