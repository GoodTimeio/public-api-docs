# Contacts API Endpoints

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
            "secondaryEmails": [
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
