# Jobs API Endpoints

* [Get Job](#get-jobsjobid)
* [Get Jobs](#get-jobs)


---

### `GET` `/jobs/:jobId`
* Returns a job from the ATS.

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
jobId | true | String | ID of the job.


#### Sample Response
```javascript
{
    "pagination": {
        next: 2,
        maxResults: 100
    },
    "result": {
        "id": "5567829a-193c-4f25-b3e3-ac42f896a1cd",
        "createdAt": "2016-11-20T04:49:20.660Z",
        "updatedAt": "2017-03-14T09:12:55.124Z",
        "closedAt": null,
        "status": "active", //active, inactive
        "name": "Regional Sales Manager",
        "offices": [
            {
                "id": "17670",
                "name": "San Francisco HQ",
                "address": "1 California St. Ste 2800, San Francisco, CA 94105"
            }
        ],
        "departments": [
            {
                "id": "26115",
                "team": "Navy",
                "department": "Military Department",
            }
        ],
        "jobAdmins": [], // list of user objects, optional
        "hiringManagers": [], // list of user objects, optional
        "interviewers": [], // list of user objects, optional
        "recruiters": [], // list of user objects, optional
        "coordinators": [], // list of user objects, optional
        "sourcers": [], // list of user objects, optional
        "keywords": [] // list of keywords or tags that pertain to this job, optional
    }
}

```


---


### `GET` `/jobs`
* Returns a list of jobs from the ATS.

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
    "pagination": {
        next: 2,
        maxResults: 100
    },
    "result": [
        {
            "id": "5567829a-193c-4f25-b3e3-ac42f896a1cd",
            "createdAt": "2016-11-20T04:49:20.660Z",
            "updatedAt": "2017-03-14T09:12:55.124Z",
            "closedAt": null, //active, inactive
            "status": "active",
            "name": "Regional Sales Manager",
            "offices": [
                {
                    "name": "San Francisco HQ",
                    "address": "1 California St. Ste 2800, San Francisco, CA 94105"
                }
            ],
            "departments": [
                {
                    "team": "Navy",
                    "department": "Military Department",
                }
            ],
            "jobAdmins": [],
            "hiringManagers": [],
            "interviewers": [],
            "recruiters": [],
            "coordinators": [],
            "keywords": []
        },
        //...
    ]
}
```



---
### `GET` `/jobs/:jobId/stages`
* Returns a stages for a job from the ATS. (For some ATS, stages are job agnotstic).

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
jobId | true | String | ID of the job.


#### Sample Response
```javascript
{
    "pagination": {
        next: 2,
        maxResults: 100
    },
    "result": [ // Should be in order
            {
                "id": "3722e88f-e4ba-44e7-a208-9a89c2d0c338",
                "name": "Recruiter Phone Screen",
                "interviewSteps": [// one or more individual meetings with candidate
                    {
                        "id": "11efa444-7605-403f-88dd-062df484c172",
                        "name": "Recruiter Phone Screen",
                        "status": "active",
                        "duration": 45, // in minutes
                        "groupId": "47fadbdb-b173-46dd-a388-54fe911cbec9",
                        "groupName": "Engineering",
                        "scorecard": {
                            "name": "Recruiter Feedback",
                            "url": "https://www.ats.com/feedback/scorecards?id=11efa444-7605-403f-88dd-062df484c172"
                        }
                    }
                ],
                "status": "active",
                "type": "video",  // optional
                "createdAt": "2016-11-20T04:49:20.660Z",
                "updatedAt": "2017-03-14T09:12:55.124Z"
            },
            {
                "id": "3722e88f-e4ba-44e7-a208-9a89c2d0c338",
                "name": "Recruiter Phone Screen",
                "interviewSteps": [
                    {
                        "id": "11efa444-7605-403f-88dd-062df484c172",
                        "name": "Recruiter Phone Screen",
                        "status": "active",
                        "duration": 45,
                        "groupId": "47fadbdb-b173-46dd-a388-54fe911cbec9",
                        "groupName": "Engineering",
                        "scorecard": {
                            "name": "Recruiter Feedback",
                            "url": "https://www.ats.com/feedback/scorecards?id=11efa444-7605-403f-88dd-062df484c172"
                        }
                    }
                ],
                "status": "active",
                "type": "video",
                "createdAt": "2016-11-20T04:49:20.660Z",
                "updatedAt": "2017-03-14T09:12:55.124Z"
            }
        ]
    }
}

```


---
