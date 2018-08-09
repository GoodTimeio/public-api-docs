# Tags API Endpoints
* Base Url `https://a.goodtime.io/api/v1`

* [Get Tags](#get-tags)


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
typeId | false | UUID | ID of the tag type
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
