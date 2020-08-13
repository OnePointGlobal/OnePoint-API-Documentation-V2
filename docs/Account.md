# Account API's

> For more information visit the [main page](../README.md)

The Account API's are made up of the following:

## Login
Before any other API is used you will need a Session Id. This API requests one.
```
URL: base/Account/Login
Method: POST
Content: { "Username":"username", "Password":"password" }
```
### Parameters

Name | Description
---- | -----------
Username | The account's user name. Cannot be blank.
Password | The account's password.

### Returns
```
{ "SessionId": "ABCCDEFG" }
```
The `SessionId` must be used in subsequent API calls by placing it in the headers as a basic authentication header.

### HTTP Statuses

Status | Description
------ | -----------
401 | The username and/or password is incorrect

## LoginWithUid
Before any other API is used you will need a Session Id. This API requests one using the User's ID (available through the account 
properties in your account).
```
URL: base/Account/LoginWithUid
Method: POST
Content: "Uid" }
```
### Parameters

Name | Description
---- | -----------
Uid | The User Id available by logging into your account and checking your account details.

### Returns
```
{ "SessionId": "ABCCDEFG" }
```
The `SessionId` must be used in subsquent calls by placing it in the header a value with the name `SessionId`.
### HTTP Statuses

Status | Description
------ | -----------
401 | The uid is invalid

## Logout
To discard a Session Id after all other API's have been used you need to logout.
```
URL: base/Logout
Header:
Authorization: Basic ABCDEFG
Method: POST
```
### Returns
nothing

