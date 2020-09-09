---
layout: default
title: Keyword
parent: Messaging
nav_order: 7
---
# Keyword

> For more information visit the [main page](../README.md)

The Keyword API's allow you to manage keywords used for managing inbound SMS messages.

## Add
Add a keyword which when detected at the beginning of an inbound message will be sent to your inbox for processing.
```
URL: base/Keyword/Add
Method: POST
{
  "Keyword": "sample string 1",
  "Type": "normal",
  "Response": "response message",
  "FinishDate": "2020-02-04T04:55:32.3122889+00:00",
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

Name | Description
---- | -----------
Keyword | The keyword which can be between 3 and 50 characters long can only contain alphanumerics
Type | The keyword type can be any one of the following - normal, stop, help or info. 
Response | For stop, help or info keywords the response is the automatic response sent to the respondent. 
FinishDate | The date the keyword expires. This should be set in the future.
MetaData | Optional | For more information on metadata check [here](MetaData.md).

### Campaigns
Campaigns allow special keywords (defined by type equal to stop, help and info) to matched to recipients. For more information on the stop process [click here](Stop.md). The campaign is picked up from the metadata by looking for the `Campaign` value. If a message is sent out to a recipient with the same campaign value then when they keywords are used that have a matching campaign Id that come from that recipient will be automatically matched and if a response is specified it will be used. The campaign will be associated with the recipient until another campaign is associated.

### Returns
```
nothing
```
### HTTP Statuses
In addition to the standard responses the following HTTP statuses can be returned:

Status | Description
------ | -----------
400 | The keyword is already registered
400 | The keyword must be between 3 and 50 characters long and can only contain alphanumerics
400 | There was a problem registering the keyword. Please contact OnePoint Global Support

## Delete
Delete a keyword.
```
URL: base/Keyword/Delete?keyword={keyword}
Method: DELETE
```
### Parameters

Name | Description
---- | -----------
keyword | The keyword that you wish to delete from your account

### Returns
```
nothing
```
### HTTP Statuses
In addition to the standard responses the following HTTP statuses can be returned:

Status | Description
------ | -----------
404 | The keyword is not found
400 | There was a problem deleting the keyword. Please contact OnePoint Global Support

## List
List all keywords associated with your account.
```
URL: base/Keyword/List
Method: GET
```

### Returns
```
[
    { "Keyword":"keyword", 
      "FinishDate", "2020-02-04T04:55:32.3122889+00:00",
      "Type": "normal",
       "MetaData": 
       [
         { "RequestID": "1234567890DEFED" },
         { "OrgID": 1010 },
         { "Instance": "ETRERT"},
         { "Campaign": 1242 },
         { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
        ]
       },
    { "Keyword":"keyword", "Type":"normal", "FinishDate", "2020-02-04T04:55:32.3122889+00:00" },
    { "Keyword":"keyword", "Type":"normal", "FinishDate", "2020-02-04T04:55:32.3122889+00:00" },
]
```

### HTTP Statuses
In addition to the standard responses the following HTTP statuses can be returned:

Status | Description
------ | -----------
400 | There are no active keywords registered

