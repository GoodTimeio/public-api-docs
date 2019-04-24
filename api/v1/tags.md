# Tags API Endpoints
* Base Url `https://a.goodtime.io/api/v1`

* [Get Tags](#get-tags)
* [Get Tags filtered by type](#get-tag-typestagtypeidtags)
* [Patch Tags](#patch-tags)

---


### `GET` `/tags`
* Returns a list of tags from GoodTime.

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
    "totalSize": 18,
    "result": [
        {
            "id": "f53eb296-4451-4495-8c08-0486a0a157af",
            "name": "iOS",
            "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac",
            "typeName": "Skills",
            "status": "active",
        }
    ]
}
```



---



### `GET` `/tags/:tagId`
* Returns a tag filtered by `:tagId`.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "iOS",
        "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac",
        "typeName": "Skills",
        "status": "active",
    }
}
```



---



### `POST` `/tags`
* Create a tag.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Request
```javascript
{
    "name": "iOS",
    "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac",
]
```

#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "iOS",
        "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac",
        "typeName": "Skills",
        "status": "active",
    }
}
```



---



### `PATCH` `/tags/:tagId`
* Update a tag by `tagId`.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Request
```javascript
{
    "name": "iOS without a type",
    "typeId": null,
]
```

#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "iOS without a type",
        "typeId": null,
        "status": "active",
    }
}
```



---



### `DELETE` `/tags/:tagId`
* Delete a tag by `tagId`.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Response
```javascript
{
    "status": "success",
    "result": {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "iOS",
        "status": "archived",
    }
}
```



---



### `GET` `/tag-types/:tagTypeId/tags`
* Returns a list of tags from GoodTime filtered by `:tagTypeId`.

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
            "name": "iOS",
            "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac",
            "typeName": "Skills",
            "status": "active",
        }
    ]
}
```



---



### `PATCH` `/tags`
* Update a list of tags and it's tagType

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Request
```javascript
[
    {
        "id": "f53eb296-4451-4495-8c08-0486a0a157af",
        "name": "iOS",
        "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac", //link a new tagType
    },
    {
        "id": "266f8c6a-e968-467f-b60e-abb873187249",
        "typeId": null, //unlink a tagtype
    }
]
```


#### Sample Response
```javascript
{
    "status": "success",
    "result": [
        {
            "id": "f53eb296-4451-4495-8c08-0486a0a157af",
            "name": "iOS",
            "typeId": "ea7260f7-1612-4e99-a8ca-fb9abae09aac",
            "typeName": "Skills",
            "status": "active",
        },
        {
            "id": "266f8c6a-e968-467f-b60e-abb873187249",
            "name": "Android",
            "typeId": null,
            "typeName": null,
            "status": "active",
        }
    ]
}
```



---