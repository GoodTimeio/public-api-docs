# Interviews API Endpoints

* [Get Interview](#get-interviewsinterviewid)
* [Get Interviews](#get-interviews)
* [Create Interview](#post-interview)
* [Update Interview](#put-interviewsinterviewid)
* [Delete Interview](#delete-interviewsinterviewid)

---

### `GET` `/interviews/:interviewId`
* Returns an interview from the CCS.

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
interviewId | true | String | ID of the interview.


#### Sample Response
```javascript
{
  "id": "2902c52a-d45b-4f0f-88f0-94351c07095f",
  "from": "2020-02-19T11:43:31+0000",
  "to": "2020-04-20T10:44:31+0000",
  "status": "new",
  "url": "www.acmecorp.com/interview/login",
  "user": "1288c45a-b41b-6a4d-128f0-94351c07889d",
  "createdAt": ":31+2020-04-20T10:44:31+0000",
  "updatedAt": ":31+2020-04-20T10:44:31+0000",
  "title": "Interview with Samir",
  "feedback": "Candidate is good in Javascript programming",
  "thumbsUp": true,
  "notes": "Assess the candidate for Javascript skillss",
  "resumeUrl": "https://www.linkedin.com/98646494",
  "interviewers": [
    "jpello@lenscorp.com"
  ],
  "resultUrl": "https://www.lenscorp.com/interview_ended",
  "candidate": {
      "name": "Samir Sanchez",
      "email": "ssanchez74839@gmail.com"
  },
  "metadata": {},
  "reportUrl": "www.acmecorp.com/interviews/2902c52a-d45b-4f0f-88f0-94351c07095f/report"
}

```


---


### `GET` `/interviews/`
* Returns a list of interviews from the CCS.

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
  "data": [
    {
      "id": "5926cbe7-b413-416f-9939-1abb30b13421",
      "from": "2020-02-19T11:43:31+0000",
      "to": "2020-04-20T10:44:31+0000",
      "status": "new",
      "url": "www.acmecorp.com/interview/login",
      "user": "1288c45a-b41b-6a4d-128f0-94351c07889d",
      "createdAt": ":31+2020-04-20T10:44:31+0000",
      "updatedAt": ":31+2020-04-20T10:44:31+0000",
      "title": "Interview with Samir",
      "feedback": "Candidate is good in Javascript programming",
      "thumbsUp": true,
      "notes": "Assess the candidate for system design concepts",
      "resumeUrl": "https://www.linkedin.com/98646494",
      "interviewers": [
        "jpello@lenscorp.com"
      ],
      "resultUrl": "https://www.lenscorp.com/interview_ended",
      "candidate": {
          "name": "Samir Sanchez",
          "email": "ssanchez74839@gmail.com"
      },
      "metadata": {},
      "reportUrl": "www.acmecorp.com/interviews/2902c52a-d45b-4f0f-88f0-94351c07095f/report"
    }
  ],
  "page_total": 1,
  "offset": 0,
  "previous": "",
  "next": "https://www.acmecorp.com/interviews?limit=1&offset=1",
  "first": "https://www.acmecorp.com/interviews?limit=1&offset=0",
  "last": "https://www.acmecorp.com/interviews?limit=1&offset=12",
  "total": 13
}
```



---



### `POST` `/interview`
* Create a new interview on the CCS

####  Header
key|value
---|---
`Authorization`| Token
`Content-Type`| `application/json`

#### POST Body
##### Sample Request
```javascript
{
  "from": "2020-02-19T11:43:31+0000",
  "to": "2020-04-20T10:44:31+0000",
  "title": "Interview with Samir",
  "notes": "Assess the candidate for Javascript programming skills",
  "resumeUrl": "https://www.linkedin.com/98646494",
  "interviewers": [
    "jpello@lenscorp.com"
  ],
  "resultUrl": "https://www.lenscorp.com/interview_ended",
  "candidate": {
    "name": "Samir Sanchez",
    "email": "ssanchez74839@gmail.com"
  },
  "send_email": false,
  "metadata": {}
}
```

#### Sample Response
```javascript
{
  "id": "5926cbe7-b413-416f-9939-1abb30b13421",
  "from": "2020-02-19T11:43:31+0000",
  "to": "2020-04-20T10:44:31+0000",
  "status": "new",
  "url": "www.acmecorp.com/interview/login",
  "user": "1288c45a-b41b-6a4d-128f0-94351c07889d",
  "createdAt": ":31+2020-04-20T10:44:31+0000",
  "updatedAt": ":31+2020-04-20T10:44:31+0000",
  "title": "Interview with Mark",
  "feedback": "Candidate is good in Javascript",
  "thumbsUp": true,
  "notes": "Assess the candidate for Javascript programming skills",
  "resumeUrl": "https://www.linkedin.com/98646494",
  "interviewers": [
    "jpello@lenscorp.com"
  ],
  "resultUrl": "https://www.lenscorp.com/interview_ended",
  "candidate": {
    "name": "Samir Sanchez",
    "email": "ssanchez74839@gmail.com"
  },
  "metadata": {},
  "reportUrl": "www.acmecorp.com/interviews/2902c52a-d45b-4f0f-88f0-94351c07095f/report"
}
```

---




### `PUT` `/interviews/:interviewId`
* Updates an interview on the CCS

####  Header
key|value
---|---
`Authorization`| Token
`Content-Type` | `application/json`

#### Sample Request
```javascript
{
  "from": "2020-02-19T11:43:31+0000",
  "to": "2020-04-20T10:44:31+0000",
  "title": "Interview with Samir",
  "notes": "Assess the candidate for Javascript programming skills",
  "resumeUrl": "https://www.linkedin.com/98646494",
  "resultUrl": "https://www.lenscorp.com/interview_ended",
  "candidate": {
    "name": "Samir Sanchez",
    "email": "ssanchez74839@gmail.com"
  },
  "send_email": false,
  "metadata": {}
}
```

#### Sample Response
```javascript
{
  "id": "5926cbe7-b413-416f-9939-1abb30b13421",
  "from": "2020-02-19T11:43:31+0000",
  "to": "2020-04-20T10:44:31+0000",
  "status": "new",
  "url": "www.acmecorp.com/interview/login",
  "user": "1288c45a-b41b-6a4d-128f0-94351c07889d",
  "createdAt": ":31+2020-04-20T10:44:31+0000",
  "updatedAt": ":31+2020-04-20T10:44:31+0000",
  "title": "Interview with Samir",
  "feedback": "Candidate is good in Javascript",
  "thumbsUp": true,
  "notes": "Assess the candidate for Javascript programming skills",
  "resumeUrl": "https://www.linkedin.com/98646494",
  "interviewers": [
    "jpello@lenscorp.com"
  ],
  "resultUrl": "https://www.lenscorp.com/interview_ended",
  "candidate": {
    "name": "Samir Sanchez",
    "email": "ssanchez74839@gmail.com"
  },
  "metadata": {},
  "reportUrl": "www.acmecorp.com/interviews/5926cbe7-b413-416f-9939-1abb30b13421/report"
}
```


---





### `DELETE` `/interviews/:interviewId`
* Deletes an interview from the CCS

####  Header
key|value
---|---
`Authorization`| Token

#### Sample Response
```javascript
{
    "status": "success",
    "requestId": "gzNjgO"
}
```



---
