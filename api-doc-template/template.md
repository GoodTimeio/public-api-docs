# DOC TITLE

* [Sample Get Endpoint](#get-sample_get_endpoint)
* [Sample Post Endpoint](#get-sample_post_endpoint)


---

### `GET` `/sample_get_endpoint`
* Endpoint Description

####  Header
key|value
---|---
`Authorization`| Token

#### GET Query
params | required | type | comment
---|---|---|---
maxResults | false | Integer | Max number of results to return. Default is 100
offset | false | Integer | Offset of results. Default is 0
query | false | String | Search query

#### Sample Response
```json
{
    "result": {}
}
```



---


### `POST` `/sample_post_endpoint`
* Endpoint Description

####  Header
key|value
---|---
`Authorization`| Token


#### POST Body
params | required | type | comment
---|---|---|---
id | true | String UUID | ID of the object.

#### Sample Response
```json
{
    "result": {}
}
```


---
