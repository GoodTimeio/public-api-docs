# Applications API Endpoints

* [Get Application](#get-applicationsapplicationid)
* [Get Applications](#get-applications)


---

### `GET` `/applications/:applicationId`
* Returns a job from the ATS.

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
applicationId | true | String | ID of the application.


#### Sample Response
```json
{
    "result": {
        "id": "5926cbe7-b413-416f-9939-1abb30b13421",
        "candidateId": "39ca6979-70d5-472c-85b8-ac6b1a20f161",
        "jobId": "5567829a-193c-4f25-b3e3-ac42f896a1cd",
        "stageId": "3722e88f-e4ba-44e7-a208-9a89c2d0c338",
        "createdAt": "2017-03-14T09:12:55.124Z",
        "updatedAt": "2017-03-14T09:12:55.124Z",
        "closedAt": null,
        "status": "active" //active, inactive
    }
}

```


---


### `GET` `/applications`
* Returns a list of applications from the ATS.

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
```json
{
    "size": 2,
    "totalSize": 2,
    "result": [
        {
            "id": "5926cbe7-b413-416f-9939-1abb30b13421",
            "candidateId": "39ca6979-70d5-472c-85b8-ac6b1a20f161",
            "jobId": "5567829a-193c-4f25-b3e3-ac42f896a1cd",
            "stageId": "3722e88f-e4ba-44e7-a208-9a89c2d0c338",
            "createdAt": "2017-03-14T09:12:55.124Z",
            "updatedAt": "2017-03-14T09:12:55.124Z",
            "closedAt": null,
            "status": "active"
        },
        ...
    ]
}
```



---
