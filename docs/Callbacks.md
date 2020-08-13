# Callbacks
Calls backs are used to handle asynchronous events in the OnePoint Global Platform. These refer to the following areas:
1. Messaging
1. Recipient Upload and validation
1. Survey Results Collection

## Messaging
When a message is sent it is possible to specify a callback method or use the one set up in your account. This callback method is used when the following events occur:
1. The message has timed out.
1. The message has been sent.
1. The message delivery fails.
1. A carrier provide an update on the progress of the message, which also include a failure.
1. A tiny URL provided by OnePoint Global is clicked on in a message that was provided.
1. A recipient replies with the keywords `STOP`, `HELP` or `INFO`.
1. A recipient responds with a keyword that is owned by you.
1. A recipient responds and you were the last account to send a message to them.

In each of these instances it is assumed that you have sent a message to that recipient. It is possible in your account to set up a call back URL which will always be used with the HTTP POST Method and provide a JSON response taking the following format:

```
{
  "Source": "12345678901",
  "Destination": "12345678901",
  "Message": "message",
  "Type": "receipt",
  "Timestamp": "2020-02-04T11:47:33.645773+00:00",
  "Inbound" : true,
  "Lookup": true,
  "Test": false,
  "Status": "sent",
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
}
```

Name | Description
---- | -----------
Source | The source of the message. This can be a short code, a long number or a branded value up to 11 characters long.
Destination | The destination of the message. This must be the full number prefixed with the country code and no leading zeros.
Message | The text message to send. This can be up to 2000 characters long.
Type | The type of call back message. For more information see below.
Timestamp | When the call back message was created by the OnePoint Global Platform.
Inbound | A boolean value indicating that the call back refers to an inbound message and source reflects the destination you sent the message to and the destination represents where you sent it from.
Lookup | A boolean value indicating whether a lookup on the destination number should be carried out before it is sent to see whether the number is a landline or mobile. If the number is a landline it will not be sent. This combines the lookup method and the send into one process for you.
Test | A boolean value that indicates whether the message should be sent or not. If set to true the message will not be sent, but the internal OnePoint Global Routing will be tested.
Status | For more information on statuses check [here](MessageStatuses.md).
MetaData | For more information on metadata check [here](MetaData.md).
MessageID | The OnePoint Global Message ID available for you to track the message in other methods and callbacks.
Carrier | The name of the carrier. This can be any valid string or the word `Unknown`
Reachable | A boolean value indicating whether the number is reachable.
NumberType | A string indicating the type of number - `Mobile`, `Landline` or `Unknown`


### Callback Types

Type | Description
---- | -----------
Receipt | An inbound message where the [status](MessageStatuses.md) reflects more information.
Lookup | A callback when the outbound message destination is check through the lookup service and fails.
Message | An inbound message that you will need to process.
Info | An inbound message that has been processed by OnePoint Global as an info message.
Help | An inbound message that has been processed by OnePoint Global as an help message.
Stop | A inbound message that has been detected as a STOP message from a recipient and has been added to the OnePoint Global STOP list.
Keyword | An inbound message that has been processed by OnePoint Global as one of your keywords.
Click | A tiny URL was clicked on. In this instance the message includes the tiny URL that was clicked on.

## Responding to Callbacks
Depending on the type of message depends on the type of response the OnePoint Global Platform expects.  

### Status Type Callbacks
For status type callbacks (Receipt, Lookup, Info, Help, Stop and Click) you can respond with an HTTP Success to complete the process. The OnePoint Global Platform will continue after any response and timeout within 30 seconds of sending the response. Any failures detected will reported through the Fallback URL and/or email to you depending on your account setup.

### Response Type Callbacks
For response type callbacks (Message, Keyword) the OnePoint Global Platform will wait for a response that include a message to be sent to the recipient of the outbound message. This response will need to take the form of the [Message/Send API method](Message.md). In these instances the `MessageID` value will remain the same as the original message.



