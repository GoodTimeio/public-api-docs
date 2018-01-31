# DOC TITLE

* [Sample Get Endpoint](#get-sample_get_endpoint)
* [Sample Post Endpoint](#get-sample_post_endpoint)


---

### `GET` `/sample_get_endpoint/:categoryId`
* Endpoint Description

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
categoryId | true | String | ID of the category

#### GET Query
params | required | type | comment
---|---|---|---
maxResults | false | Integer | Max number of results to return. Default is 100
offset | false | Integer | Offset of results. Default is 0
query | false | String | Search query
createdAtMin | false | String ISO Time | Lower bound (inclusive) of the createdAt time.
createdAtMax | false | String ISO Time | Upper bound (exclusive) of the createdAt time.
updatedAtMin | false | String ISO Time | Lower bound (inclusive) of the updatedAt time.
updatedAtMax | false | String ISO Time | Upper bound (exclusive) of the updatedAt time.

#### Sample Response
```json
{
    "result": {}
}
```



---


### `POST` `/sample_post_endpoint/:objectId`
* Endpoint Description

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
objectId | true | String | ID of the object.

#### POST Body
params | required | type | comment
---|---|---|---
name | true | String | Name of the object

#### Sample Response
```json
{
    "result": {}
}
```


---
