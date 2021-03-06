# Tag Types API Endpoints
* Base Url `https://a.goodtime.io/api/v1`

* [Get Tag Types](#get-tag-types)
* [Get a single Tag Type](#get-tag-typestagtypeid)
* [Create a Tag Type](#post-tag-types)
* [Update a Tag Type](#patch-tag-typestagtypeid)
* [Archive a Tag Type](#delete-tag-typestagtypeid)


---


### `GET` `/tag-types`
* Returns a list of tag types from GoodTime.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### GET Query
params | required | type | comment
---|---|---|---
maxResults | false | Integer | Max number of results to return. Default is 100
offset | false | Integer | Offset of results. Default is 0
status | false | String | 'active' or 'archived'
query | false | string | Search by tag name
createdAtMin | false | String ISO Time | Lower bound (inclusive) of the createdAt time.
createdAtMax | false | String ISO Time | Upper bound (exclusive) of the createdAt time.
updatedAtMin | false | String ISO Time | Lower bound (inclusive) of the updatedAt time.
updatedAtMax | false | String ISO Time | Upper bound (exclusive) of the updatedAt time.

#### Sample Response
```javascript
{
    "status": "success",
    "size": 1,
    "totalSize": 1,
    "result": [
        {
            "id": "f53eb296-4451-4495-8c08-0486a0a157af",
            "name": "Skills",
            "status": "active",
        }
    ]
}
```



---



### `GET` `/tag-types/:tagTypeId`
* Returns a single tag type from GoodTime.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Response
```javascript
{
    "status": "success",
    "size": 1,
    "totalSize": 1,
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "Skills",
        "status": "active",
    }
}
```



---



### `PATCH` `/tag-types/:tagTypeId`
* Update a single tag type

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))
`Content-Type`| `application/json`

#### Sample Request
```javascript
{
    "name": "New name",
}
```


#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "New name",
        "status": "active",
    }
}
```



---



### `POST` `/tag-types`
* Create a tag type

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))
`Content-Type`| `application/json`

#### Sample Request
```javascript
{
    "name": "Tag type name",
    "status": "archived" // the status field is optional. if it is not passed in the body, the default status is "active"
}
```


#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "Tag type name",
        "status": "archived",
    }
}
```



---



### `DELETE` `/tag-types/:tagTypeId`
* Archive a tag type

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Request
```javascript
// no body needed
```


#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "Old tag Type name",
        "status": "archived",
    }
}
```



---
