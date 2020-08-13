# Usage
Messaging usage.

## Message History
Retrieve a message history for all messages sent and received for your account.
```
URL: base/Usage/History
Method: POST
{
    "Limit": 10,
    "Pagesize": 2,
    "DateRange": { "From": "2020-02-04T11:47:33.645773+00:00", "To": "2020-02-06T11:47:33.645773+00:00" },
    "Source" : "Source",
    "Destination": "Destination",
    "Inbound": true,
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

### Parameters

Name | Type | Description
---- | ---- | -----------
Limit | Optional (default: All messages) | The total number of messages to receive. This could be useful if you are not set up to receive the total number for any particular reason.
Pagesize | Optional (default: 10) | The number of messages to return in one batch.
DateRange | Optional (default: all dates) | The start date and finish date that the messages were sent and received.
Source | Optional (default: all sources) | The source of the message. This is also dependant on the inbound flag.
Destination | Optional (default: all destinations) | The destination of the message. This is dependant on the inbound flag.
MetaData | Optional (default: all MetaData) | It is possible to filter on the metadata and any or all of the elements of the metadata.

### Returns

```
{
  "Page":1,
  "Messages" : [
    {
        "Source": "12345678901",
        "Destination": "12345678901",
        "Message": "message",
        "Timestamp": "2020-02-04T11:47:33.645773+00:00",
        "Inbound" : true,
        "Lookup": true,
        "Test": false,
        "Status": "sent",
        "Segments": 1,
        "MetaData": 
            [
                { "RequestID": "1234567890DEFED" },
                { "OrgID": 1010 },
                { "Instance": "ETRERT"},
                { "Campaign": 1242 },
                { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
            ],
        "MessageID": "MS1312312312323",
        "Carrier": "EE",
        "Reachable": true,
        "NumberType": "Mobile"    
    },
    ...
  ]
}

```