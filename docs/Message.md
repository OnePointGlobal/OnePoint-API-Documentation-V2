# Message
The Message API's allow you to send SMS messages across a global network with the addition of supporting methods for lookup and validation of mobile numbers.

## Sending a Message
Send an SMS message anywhere in the world.
```
URL: base/Message/Send
Method: POST
{
  "Source": "12345678901",
  "Destination": "12345678901",
  "Message": "message",
  "Reply": true,
  "When": "2020-02-04T11:47:33.645773+00:00",
  "Window": [{ From: "09:00", To: "16:00", Days: "1,2,3,4,5"}],
  "Callback": "https://yourco.com/api/messagetracker",
  "Lookup": true,
  "Test": false,
  "Timeout": "4320",
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
Source | Mandatory | The source of the message. This can be a short code, a long number or a branded value up to 11 characters long.
Destination | Mandatory | The destination of the message. This must be the full number prefixed with the country code and no leading zeros.
Message | Message | The text message to send. This can be up to 2000 characters long.
Reply | Optional (Default: false) | A boolean value indicating whether the message can be replied to or not. If this is true then the destination may be replaced depending on destination value and the route the message has to take to get to its destination.
When | Optional (Default: now) | A date and time indicating when the message should be sent. This allows the opportunity to submit a message to be sent at a later date.
Window | Optional (Default: any time) | An array of windows that the message can be sent. The allows you to specify different windows as to when the message can be sent. Each window follows these [rules](Windows.md).
Callback | Optional (Default: Account Settings) | There is the ability to override the standard callback method associate with you r account. For more information on callbacks check here.
Lookup | Optional (Default: false) | A boolean value indicating whether a lookup on the destination number should be carried out before it is sent to see whether the number is a landline or mobile. If the number is a landline it will not be sent. This combines the lookup method and the send into one process for you.
Test | Optional (Default: false) | A boolean value that indicates whether the message should be sent or not. If set to true the message will not be sent, but the internal OnePoint Global Routing will be tested.
Timeout | Options (Default: 4320) | a numeric value defining the number of minutes the OnePoint Global Platform will maintain a message to be replied to. The default is 3 days.
MetaData | Optional | For more information on metadata check [here](MetaData.md).
Macros | Optional | A set of values to use as insert references for macros. For more information on this please check [here](Macros.md).

### Returns
```
{
    "MessageID": "MS1312312312323",
    "Status": "sent",
    "Carrier": "EE",
    "Reachable": true,
    "NumberType": "Mobile"
}
```

### Return Values

Name | Description
---- | -----------
MessageID | The OnePoint Global Message ID available for you to track the message in other methods and callbacks.
Status | The initial status of the send. This can be any one of the following [values](MessageStatuses.md).

If a lookup is performed as part of the process the following return values will be included:

Name | Description
---- | -----------
Carrier | The name of the carrier. This can be any valid string or the word `Unknown`
Reachable | A boolean value indicating whether the number is reachable.
NumberType | A string indicating the type of number - `Mobile`, `Landline` or `Unknown`


### HTTP Statuses
In addition to the standard responses the following HTTP statuses can be returned:

Status | Description
------ | -----------
400 | The destination number is invalid
400 | The destination and source cannot be the same
400 | The message length must be greater than zero
400 | There was a problem sending the message. Please refer to the status

## Kill
Kill off any outstanding activity with one or some message, by providing an array or information.
```
URL: base/Message/Kill
Method: POST
{
  [
    {
      "Destination": "12345678901",
      "MetaData": 
      [
        { "RequestID": "1234567890DEFED" },
        { "OrgID": 1010 },
        { "Instance": "ETRERT"},
        { "Campaign": 1242 },
        { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
      ],
      "Callback": "https://yourco.com/api/messagetracker",
    },
    ....
  ]
}
```
### Parameters

Name | Type | Description
---- | ---- | -----------
Destination | Mandatory | The destination of the message. This must be the full number prefixed with the country code and no leading zeros.
Callback | Optional (Default: Account Settings) | There is the ability to override the standard callback method associate with you r account. For more information on callbacks check here.
MetaData | Optional | For more information on metadata check [here](MetaData.md).

### Returns 
Nothing

## Lookup
Lookup a number on the network to see whether it is reachable and whether it is a mobile number.
```
URL: base/Message/Lookup
Method: POST
{
  "Number": "12345678901",
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
Number | The number to lookup
MetaData | Optional | For more information on metadata check [here](MetaData.md).

### Returns
```
{
  "Number": "01234567890",
  "Carrier": "EE",
  "Message": "Success Message",
  "Reachable": true,
  "Status": "Success",
  "NumberType": "Mobile"
}
```
### Return Parameters

Name | Description
---- | -----------
Number | The number that was looked up
Carrier | The name of the carrier. This can be any valid string or the word `Unknown`
Message | A status message which varies depending on the success of the lookup and the carrier involved.
Reachable | A boolean value indicating whether the number is reachable.
Status | A string indicating the result of the lookup. Either `Success` or `Failure`
NumberType | A string indicating the type of number - `Mobile`, `Landline` or `Unknown`

### HTTP Statuses
In addition to the standard responses the following HTTP statuses can be returned:

Status | Description
------ | -----------
400 | There was a problem with the Lookup. Please check your request and try again

