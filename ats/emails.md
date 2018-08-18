# Emails API Endpoints


* [Create Email](#post-email)


---


### `POST` `/email`
* Add a new email on the ATS

####  Header
key|value
---|---
`Authorization`| Token

#### POST Body
##### Sample Request
```javascript
{
    {
        "user_id": "6daad971-a949-49ab-b5ad-f475b09e17d3",
        "to": "candidate@example.com",
        "from": "recruiter@example.com",
        "cc": ["manager@example.com"],
        "subject": "Interview Scheduled",
        "body": "An interview has been scheduled for tomorrow."
    }
}
```


---
