# Candidates API Endpoints

* [Get Candidate](#get-candidatescandidateid)
* [Get Candidates](#get-candidates)


---

### `GET` `/candidates/:candidateId`
* Returns a candidate from the ATS.

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
candidateId | true | String | ID of the candidate.


#### Sample Response
```javascript
{
    "result": {
        "id": "2902c52a-d45b-4f0f-88f0-94351c07095f",
        "givenName": "Ariel",
        "familyName": "Peterson",
        "nickname": "Ari",
        "title": "Researcher",
        "companY": "MIT",
        "candidateUrl": "https://www.ats.com/candidates/2902c52a",
        "photoUrl": "https://www.photos.com/Vjs23j20fHfkdk",
        "phoneNumbers": [
            {
                "isPrimary": true, // only supports 1 primary numbe
                "type": "mobile", // options: home, mobile, work, other
                "phoneNumber": "5121112222",
                "formattedNumber": "+1 (512) 111-2222",
                "optInForContact": true,  // if the user has opted in to receive contact information on this phone
                "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                "optInMeta": "Checkbox sign in flow via ATS Login" // an optional string field to pass in any additional opt in data
            }
        ],
        "emails": [ // one or more candidate email addresses
            {
                "isPrimary": true, // only supports 1 primary email
                "type": "school", // options: personal, school, work, other
                "email": "ari@mit.edu",
                "optInForContact": true, // if the user has opted in to receive contact information on this phone
                "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                "optInMeta": "Checkbox sign in flow via ATS Login" // an optional string field to pass in any additional opt in data
            }
        ],
        "links": [
            {
                "type": "linkedin",
                "value": "https://www.linkedin.com/in/ari"
            },
            {
                "type": "skype",
                "value": "arip"
            }
        ],
        "createdAt": "2017-03-14T09:12:55.124Z",
        "updatedAt": "2017-03-14T09:12:55.124Z",
        "status": "active" // we will stop syncing inactive candidates
    }
}

```


---


### `GET` `/candidates`
* Returns a list of candidates from the ATS.

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
            "givenName": "Ariel",
            "familyName": "Peterson",
            "nickname": "Ari",
            "title": "Researcher",
            "companY": "MIT",
            "candidateUrl": "https://www.ats.com/candidates/2902c52a",
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
                    "type": "school",
                    "email": "ari@mit.edu",
                    "optInForContact": true,
                    "optInTimeStamp": "2017-03-14T09:12:55.124Z",
                    "optInMeta": "Checkbox sign in flow via ATS Login"
                }
            ],
            "links": [
                {
                    "type": "linkedin",
                    "value": "https://www.linkedin.com/in/ari"
                },
                {
                    "type": "skype",
                    "value": "arip"
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
