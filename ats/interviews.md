# Interviews API Endpoints

* [Get Interview](#get-interviewsinterviewid)
* [Get Interviews](#get-interviews)
* [Create Interview](#post-interviews)
* [Update Interview](#patch-interviewsinterviewid)


---

### `GET` `/interviews/:interviewId`
* Returns an interview from the ATS.

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
    "result": {
        "id": "6daad971-a949-49ab-b5ad-f475b09e17d3",
        "startTime": "2018-02-01T13:00:00.000Z", //ISO Time String
        "endTime": "2018-02-01T15:00:00.000Z",
        "title": "James Hunt SF Software Engineer interview",
        "location": "SF HQ",
        "status": "confirmed", // confirmed, canceled
        "applicationId": "653ad42e-2fae-4623-87e7-1f7bcee70992",
        "jobId": "959931bd-d9fb-42d7-b775-391b4ea35a97",
        "stageId": "9c4564f3-195e-4261-934d-6147112d7f9b",
        "calendarType": "google", // google, office365
        "calendarId": "afb3c0be7a72@group.calendar.google.com",
        "calendarEventId": "94893d5d113be4bd27f75ba1",
        "iCalUID": "f703a054bada@google.com",
        "createdAt": "2017-03-14T09:12:55.124Z",
        "updatedAt": "2017-03-14T09:12:55.124Z",
        "events": [
            {
                "id": "e2a308a4-db04-47c5-a68e-6706ac3ba710",
                "eventId": "9af79b8d-b1a5-4dfe-8e54-56d16df1336c", // ID from job.stages[].events[].id
                "title": "Technical Interview 1",
                "location": "12F Interview Room",
                "status": "confirmed", //confirmed, canceled
                "startTime": "2018-02-01T13:00:00.000Z",
                "endTime": "2018-02-01T14:00:00.000Z",
                "calendarType": "google", // google, office365
                "calendarId": "81836bfd9e6a@group.calendar.google.com",
                "calendarEventId": "81836bfd9e6afc7af73083fc",
                "iCalUID": "0ce6af51f5d4@google.com",
                "createdAt": "2017-03-14T09:12:55.124Z",
                "updatedAt": "2017-03-14T09:12:55.124Z",
                "interviewers": [
                    {
                        // User object
                    },
                    //...
                ]
            },
            //...
        ]
    }
}

```


---


### `GET` `/interviews`
* Returns a list of interviews from the ATS.

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
            "id": "6daad971-a949-49ab-b5ad-f475b09e17d3",
            "startTime": "2018-02-01T13:00:00.000Z",
            "endTime": "2018-02-01T15:00:00.000Z",
            "title": "James Hunt SF Software Engineer interview",
            "location": "SF HQ",
            "status": "confirmed", // confirmed, canceled
            "applicationId": "653ad42e-2fae-4623-87e7-1f7bcee70992",
            "jobId": "959931bd-d9fb-42d7-b775-391b4ea35a97",
            "stageId": "9c4564f3-195e-4261-934d-6147112d7f9b",
            "calendarType": "google", // google, office365
            "calendarId": "afb3c0be7a72@group.calendar.google.com",
            "calendarEventId": "94893d5d113be4bd27f75ba1",
            "iCalUID": "f703a054bada@google.com",
            "createdAt": "2017-03-14T09:12:55.124Z",
            "updatedAt": "2017-03-14T09:12:55.124Z",
            "events": [
                {
                    "id": "e2a308a4-db04-47c5-a68e-6706ac3ba710",
                    "eventId": "9af79b8d-b1a5-4dfe-8e54-56d16df1336c", // ID from job.stages[].events[].id
                    "title": "Technical Interview 1",
                    "location": "12F Interview Room",
                    "status": "confirmed", //confirmed, canceled
                    "startTime": "2018-02-01T13:00:00.000Z",
                    "endTime": "2018-02-01T14:00:00.000Z",
                    "calendarType": "google", // google, office365
                    "calendarId": "81836bfd9e6a@group.calendar.google.com",
                    "calendarEventId": "81836bfd9e6afc7af73083fc",
                    "iCalUID": "0ce6af51f5d4@google.com",
                    "createdAt": "2017-03-14T09:12:55.124Z",
                    "updatedAt": "2017-03-14T09:12:55.124Z",
                    "interviewers": [
                        {
                            // User object
                        },
                        //...
                    ]
                },
                //...
            ]
        }
    ]
}
```



---


### `POST` `/interviews`
* Add a new interview on the ATS

####  Header
key|value
---|---
`Authorization`| Token

#### POST Body
##### Sample Request
```javascript
{
    "id": "6daad971-a949-49ab-b5ad-f475b09e17d3",
    "startTime": "2018-02-01T13:00:00.000Z",
    "endTime": "2018-02-01T15:00:00.000Z",
    "title": "James Hunt SF Software Engineer interview",
    "location": "SF HQ",
    "status": "confirmed", // confirmed, canceled
    "applicationId": "653ad42e-2fae-4623-87e7-1f7bcee70992",
    "jobId": "959931bd-d9fb-42d7-b775-391b4ea35a97",
    "stageId": "9c4564f3-195e-4261-934d-6147112d7f9b",
    "calendarType": "google", // google, office365
    "calendarId": "afb3c0be7a72@group.calendar.google.com",
    "calendarEventId": "94893d5d113be4bd27f75ba1",
    "iCalUID": "f703a054bada@google.com",
    "events": [
        {
            "id": "e2a308a4-db04-47c5-a68e-6706ac3ba710",
            "eventId": "9af79b8d-b1a5-4dfe-8e54-56d16df1336c", // ID from job.stages[].events[].id
            "title": "Technical Interview 1",
            "location": "12F Interview Room",
            "status": "confirmed", //confirmed, canceled
            "startTime": "2018-02-01T13:00:00.000Z",
            "endTime": "2018-02-01T14:00:00.000Z",
            "calendarType": "google", // google, office365
            "calendarId": "81836bfd9e6a@group.calendar.google.com",
            "calendarEventId": "81836bfd9e6afc7af73083fc",
            "iCalUID": "0ce6af51f5d4@google.com",
            "interviewers": [
                {
                    "id": "7aaa3d0f-f7df-4ded-ace8-61a1982241e5"
                },
                //...
            ]
        },
        //...
    ]
}
```

---


### `PATCH` `/interviews/:interviewId`
* Update an interview on the ATS

####  Header
key|value
---|---
`Authorization`| Token

#### Path Params
params | required | type | comment
---|---|---|---
interviewId | true | String | ID of the interview.

#### POST Body

#### Sample Request
```javascript
{
    "id": "6daad971-a949-49ab-b5ad-f475b09e17d3",
    "startTime": "2018-02-01T13:00:00.000Z",
    "endTime": "2018-02-01T15:00:00.000Z",
    "title": "James Hunt SF Software Engineer interview",
    "location": "SF HQ",
    "status": "confirmed", // confirmed, canceled
    "applicationId": "653ad42e-2fae-4623-87e7-1f7bcee70992",
    "jobId": "959931bd-d9fb-42d7-b775-391b4ea35a97",
    "stageId": "9c4564f3-195e-4261-934d-6147112d7f9b",
    "calendarType": "google", // google, office365
    "calendarId": "afb3c0be7a72@group.calendar.google.com",
    "calendarEventId": "94893d5d113be4bd27f75ba1",
    "iCalUID": "f703a054bada@google.com",
    "events": [
        {
            "id": "e2a308a4-db04-47c5-a68e-6706ac3ba710",
            "eventId": "9af79b8d-b1a5-4dfe-8e54-56d16df1336c", // ID from job.stages[].events[].id
            "title": "Technical Interview 1",
            "location": "12F Interview Room",
            "status": "confirmed", //confirmed, canceled
            "startTime": "2018-02-01T13:00:00.000Z",
            "endTime": "2018-02-01T14:00:00.000Z",
            "calendarType": "google", // google, office365
            "calendarId": "81836bfd9e6a@group.calendar.google.com",
            "calendarEventId": "81836bfd9e6afc7af73083fc",
            "iCalUID": "0ce6af51f5d4@google.com",
            "interviewers": [
                {
                    "id": "7aaa3d0f-f7df-4ded-ace8-61a1982241e5"
                },
                //...
            ]
        },
        //...
    ]
}
```


---
