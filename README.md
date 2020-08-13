# Welcome to the OnePoint Global API V2.0
Welcome to the OnePoint API Documentation. This is for general use of OnePoint Globals Open API. Using this RESTful API you can send and receive SMS messages, track the delivery of sent messages, retrieve the message history, manage keywords and surveys.

## Base URL
All URLs referenced in this documentation have the following base:
```
https://api.1pt.mobi/gateway2/api
```

The API is offered over HTTPS, HTTP is not supported in order to support a secure platform.

## Authentication
OnePoint's API requires authentication to be achieved to gain a session that is then used for subsequent requests to the API. It is then recommended that you discard the session in a proper manner.

Authentication is achieved using the following API:
```
URL: base/Account/Login
Method: POST
Content: { "Username":"username", "Password":"password" }
```

All API's will return either a success status (200) or a failure status which can vary depending on the error. If the above API is successful then it will return a Session ID in the following format:
```
{ "SessionId": "ABCCDEFG" }
```

The Session ID must be used in subsequent API calls by placing it in the headers as a basic authentication header. For example, to send an SMS the following API would be used:
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
  "When": "2020-02-04T11:47:33.645773+00:00"
  "Window": [{ From: "09:00", To: "16:00", Days: "1,2,3,4,5"}]
}
```

When a session is no longer required then the following API will remove it:
```
URL: base/Account/Logout
Header:
Authorization: Basic ABCDEFG
Method: POST
```

## Statuses
Every API will return a status which can be one of the following:

Status | Description
------ | -----------
200	| Success
400	| Bad request. the HTTP message will vary depending on the type of problem.
401 | Unauthorized. The session details cannot be successfully authenticated for the API method.

> Any other Status values are included in the documentation for the API method. 

## Meta Data
It is possible to provide meta data with any API method (where appropriate) in order to help track your messaging more effectively. For more information on this refer to the [Meta Data documentation](docs/MetaData.md).

## Call Backs
OnePoint Global offers the ability for callbacks on many of the methods. For more information check [here](docs/Callbacks.md).

## Macros
OnePoint Global makes it possible to include macros in your messaging that give access to powerful tools such as the OnePoint Global Tiny URL Service. For more information check [here](docs/Macros.md).

## API's
The API's are split into the following:

1. [Account](docs/Account.md) - Session Management
1. Keyword - Keyword Management
1. TinyUrl - TinyUrl Creation
1. [Message](docs/Message.md) - SMS Message Management
1. Survey - Survey Results
1. Recipient - Upload Recipients with de-duplication and mobile number validation
1. [Usage](docs/Usage.md) - Usage reporting

## Reporting Issues
OnePoint Global is focused on continually improving the quality of its software where our customer's satisfaction is our No 1 priority. If you experience any issues then please report it through the public GitHub Issues. If you believe the issue is related to the security of the service then please contact us directly.
