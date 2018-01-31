# Users API Endpoints

* [Get User](#get-usersuserid)
* [Get Users](#get-users)


---

### `GET` `/users/:userId`
* Returns a user from the ATS.

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
userId | true | String | ID of the user.


#### Sample Response
```javascript
{
    "result": {
        "id": "2902c52a-d45b-4f0f-88f0-94351c07095f",
        "givenName": "William",
        "familyName": "Doe",
        "nickname": "Bill",
        "title": "Software Engineer",
        "company": "Example Inc.",
        "photoUrl": "https://www.photos.com/Vjs23j20fHfkdk",
        "phoneNumbers": [
            {
                "isPrimary": true, // There should be only 1 primary
                "type": "mobile", // options: home, mobile, work, other
                "phoneNumber": "5121112222",
                "formattedNumber": "+1 (512) 111-2222",
                "optInForContact": true, // if the user has opted in to receive contact information on this phone
                "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                "optInMeta": "Checkbox sign in flow via ATS Login" // an optional string field to pass in any additional opt in data
            }
        ],
        "emails": [
            {
                "isPrimary": true, // There should be only 1 primary
                "type": "work", // options: personal, school, work, other
                "email": "bill@example.com", // if the user has opted in to receive contact information on this phone
                "optInForContact": true,
                "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                "optInMeta": "Checkbox sign in flow via ATS Login" // an optional string field to pass in any additional opt in data
            }
        ],
        "links": [
            {
                "type": "linkedin",
                "value": "https://www.linkedin.com/in/bill"
            },
            {
                "type": "skype",
                "value": "bill"
            }
        ],
        "createdAt": "2017-03-14T09:12:55.124Z",
        "updatedAt": "2017-03-14T09:12:55.124Z",
        "status": "active"
    }
}

```


---


### `GET` `/users`
* Returns a list of users from the ATS.

####  Header
key|value
---|---
`Authorization`| Token

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
    "size": 2,
    "totalSize": 2,
    "result": [
        {
            "id": "2902c52a-d45b-4f0f-88f0-94351c07095f",
            "givenName": "William",
            "familyName": "Doe",
            "nickname": "Bill",
            "title": "Software Engineer",
            "company": "Example Inc.",
            "photoUrl": "https://www.photos.com/Vjs23j20fHfkdk",
            "phoneNumbers": [
                {
                    "isPrimary": true,
                    "type": "mobile",
                    "phoneNumber": "5121112222",
                    "formattedNumber": "+1 (512) 111-2222",
                    "optInForContact": true,
                    "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                    "optInMeta": "Checkbox sign in flow via ATS Login"
                }
            ],
            "emails": [
                {
                    "isPrimary": true,
                    "type": "work",
                    "email": "bill@example.com",
                    "optInForContact": true,
                    "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                    "optInMeta": "Checkbox sign in flow via ATS Login"
                }
            ],
            "links": [
                {
                    "type": "linkedin",
                    "value": "https://www.linkedin.com/in/bill"
                },
                {
                    "type": "skype",
                    "value": "bill"
                }
            ],
            "createdAt": "2017-03-14T09:12:55.124Z",
            "updatedAt": "2017-03-14T09:12:55.124Z",
            "status": "active"
        },
        //...
    ]
}
```



---
