---
layout: default
title: Home
nav_order: 1
---
# Welcome to the OnePoint Global API
Welcome to the OnePoint Global API Documentation. This is for general use of OnePoint Globals Open API. Using this RESTful API you can send and receive SMS messages, track the delivery of sent messages, retrieve the message history, manage keywords and surveys.

## Base URL
All URLs referenced in this documentation have the following base:
```
https://sms.1pt.mobi/api
```

The API is offered over HTTPS, HTTP is not supported in order to support a secure platform.

## Authentication
OnePoint Global Platform supports the use of HMAC. For more information please [click here](docs/Security.md).

## HTTP Statuses
Every API will return a status which can be one of the following:

Status | Description
------ | -----------
200	| Success
400	| Bad request. the HTTP message will vary depending on the type of problem.
401 | Unauthorized. The session details cannot be successfully authenticated for the API method.

> Any other Status values are included in the documentation for the API method. 

## Meta Data
It is possible to provide meta data with any API method (where appropriate) in order to help track your messaging more effectively. For more information on this refer to the [Metadata Documentation](docs/MetaData.md).

## Call Backs
OnePoint Global offers the ability for callbacks on many of the methods. For more information check [here](docs/Callbacks.md).

## Macros
OnePoint Global makes it possible to include macros in your messaging that give access to powerful tools such as the OnePoint Global Tiny URL Service. For more information check [here](docs/Macros.md).

## API's
The API's are split into the following:

1. [Keyword](docs/Keyword.md) - Keyword Management
1. [TinyUrl](docs/TinyUrl.md) - TinyUrl Creation
1. [Message](docs/Message.md) - SMS Message Management
1. [Survey](docs/Survey.md) - Survey Results
1. [Recipient](docs/Recipient.md) - Upload Recipients with de-duplication and mobile number validation
1. [Usage](docs/Usage.md) - Usage reporting

## Frequently Asked Questions
After you have read all the documentation we have tried to answer all your frequently asked questions [here](docs/Faq.md).

## Reporting Issues
OnePoint Global is focused on continually improving the quality of its software where our customer's satisfaction is our No 1 priority. If you experience any issues or have any question then please report it through the public [GitHub Issues](https://github.com/OnePointGlobal/OnePoint-API-Documentation-V2/issues). If you believe the issue is related to the security of the service then please contact us directly.
