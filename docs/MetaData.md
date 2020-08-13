# Metadata
To enhance the API experience and make it easier to track your data held within the OnePoint Global Platform we offer the ability to supply metadata along with any API method (where appropriate). This meta data is then returned in any call backs or along with data provision (for example collecting a message history).

Meta Data takes the form of a JSON array and can contain any number of entries support your needs. For example:
```
[
    { "RequestID": "1234567890DEFED" },
    { "OrgID": 1010 },
    { "Instance": "ETRERT"},
    { "Campaign": 1242 },
    { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
]
```

You will see from the example that the data can contain strings, numbers and dates. To supply with your API method you reference the metadata element in the JSON structure. For example, when sending an SMS message:
```
URL: base/Message/Send
Header:
Authorization: Basic ABCDEFG
Method: POST
Content:
{
  "Source": "12345678901",
  "Destination": "12345678901",
  "Message": "message",
  "Reply": true,
  "When": "2020-02-04T11:47:33.645773+00:00",
  "Window": [{ From: "09:00", To: "16:00", Days: "1,2,3,4,5"}],
  "Callback": "https://yourco.com/api/messagetracker",
  "MetaData": 
    [
        { "RequestID": "1234567890DEFED" },
        { "OrgID": 1010 },
        { "Instance": "ETRERT"},
        { "Campaign": 1242 },
        { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
    ]
}
```

## Callbacks
When a callback is triggered along with the standard information the additional metadata data is provided. For example (based on the above example):
```
URL: https://yourco.com/api/messagetracker
Header:
Authorization: Basic ABCDEFG
Method: POST
Content:
{
  "Source": "12345678901",
  "Destination": "12345678901",
  "Message": "the response",
  "When": "2020-02-04T11:47:33.645773+00:00",
  "MessageID": "MS1312312312323",
  "MetaData": 
    [
        { "RequestID": "1234567890DEFED" },
        { "OrgID": 1010 },
        { "Instance": "ETRERT"},
        { "Campaign": 1242 },
        { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
    ]
}

```
