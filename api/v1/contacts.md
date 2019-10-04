# Contacts API Endpoints
* Base Url `https://a.goodtime.io/api/v1`

* [Get Contacts](#get-contacts)


---


### `GET` `/contacts`
* Returns a list of contacts from GoodTime.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### GET Query
params | required | type | comment
---|---|---|---
maxResults | false | Integer | Max number of results to return. Default is 100
offset | false | Integer | Offset of results. Default is 0
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
            "id": "7bc48d02-bbc2-4bdd-ae3e-c23b7479efd7",
            "givenName": "Geoff",
            "familyName": "Kyle",
            "primaryEmail": "gkyle@goodtime.io",
            "emails": [
                "gkyle@goodtime.io",
                "geoff@goodtime.io"
            ],
            "notes": "This is a note example",
            "atsUserId": "88723",
            "settings": {
                "interviewAvailabilityPerDay": 1000000,
                "interviewAvailabilityPerWeek": 1000000
            },
            "status": "active",
            "tags": [{
                "id": "f53eb296-4451-4495-8c08-0486a0a157af",
                "name": "iOS",
                "type": "Skill",
                "status": "active"
            }]
        }
    ]
}
```



---




### `GET` `/contacts/:id/tags`
* Returns a list of tags associated to the contact by `:id`.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Response
```javascript
{
    "status": "success",
    "requestId": "jLIpDB",
    "result": [
        {
            "id": "1b697008-502f-42bd-836c-ca0813ea4290",
            "name": "SF",
            "typeId": "21ea6b07-7fff-452b-ab05-4734505d8eaf",
            "status": "active"
        },
        {
            "id": "3c83269d-5f37-4607-85af-6cf0c33a284d",
            "name": "Engineering",
            "typeId": "56fe0869-c029-4f16-a71f-25fea308ad05",
            "status": "active"
        }
    ]
}
```



---




### `PUT` `/contacts/:id/tags`
* Returns a list of UserToTag objects after adding a list of tags to the contact by `:id`.

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Request
```javascript
[
    {
        "id": "1b697008-502f-42bd-836c-ca0813ea4290",
        "name": "SF",
        "typeId": "21ea6b07-7fff-452b-ab05-4734505d8eaf",
        "status": "active"
    },
    {
        "id": "3c83269d-5f37-4607-85af-6cf0c33a284d",
        "name": "Engineering",
        "typeId": "56fe0869-c029-4f16-a71f-25fea308ad05",
        "status": "active"
    }
]
```

#### Sample Response
```javascript
{
    "0": {
        "createdAt": "2019-10-04T18:57:52.742Z",
        "updatedAt": "2019-10-04T18:57:52.742Z",
        "TagId": "1b697008-502f-42bd-836c-ca0813ea4290",
        "UserId": "02b6bb8f-ccd8-4665-9409-9cbcca78de15"
    },
    "1": {
        "createdAt": "2019-10-04T18:57:52.742Z",
        "updatedAt": "2019-10-04T18:57:52.742Z",
        "TagId": "3c83269d-5f37-4607-85af-6cf0c33a284d",
        "UserId": "02b6bb8f-ccd8-4665-9409-9cbcca78de15"
    },
    "status": "success",
    "requestId": "gAHf2q"
}
```



---





### `Delete` `/contacts/:id/tags/:tagId`
* Removes a tag from a contact and returns a 1 for the removed tag

####  Header
key|value
---|---
`Authorization`| Basic authorization (`Basic ` + base64(`api key` + `:`))

#### Sample Response
```javascript
{
    "status": "success",
    "requestId": "gzNjgO"
}
```



---