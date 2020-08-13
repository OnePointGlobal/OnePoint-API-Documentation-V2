# Recipient

> For more information visit the [main page](../README.md)

The Recipient API's allow you to add recipients into a recipient list.

## Add
Add recipients to a recipient list.
```
URL: base/Recipient/Add
Method: POST
{
  "ListName": "sample string 1",
  "RecipientList": [
    {
      "Title": "sample string 1",
      "FirstName": "sample string 2",
      "LastName": "sample string 3",
      "MobileNumber": "sample string 4",
      "EmailAddress": "sample string 5",
      "User1": "sample string 6",
      "User2": "sample string 7",
      "User3": "sample string 8",
      "User4": "sample string 9",
      "User5": "sample string 10",
      "User6": "sample string 11",
      "User7": "sample string 12",
      "User8": "sample string 13",
      "User9": "sample string 14",
      "User10": "sample string 15",
      "When": "2020-02-04T16:23:43.6826425+00:00",
      "LookupTest": true
    },
    {
      "Title": "sample string 1",
      "FirstName": "sample string 2",
      "LastName": "sample string 3",
      "MobileNumber": "sample string 4",
      "EmailAddress": "sample string 5",
      "User1": "sample string 6",
      "User2": "sample string 7",
      "User3": "sample string 8",
      "User4": "sample string 9",
      "User5": "sample string 10",
      "User6": "sample string 11",
      "User7": "sample string 12",
      "User8": "sample string 13",
      "User9": "sample string 14",
      "User10": "sample string 15",
      "When": "2020-02-04T16:23:43.6826425+00:00",
      "LookupTest": true
    }
  ],
  "Duplication": {
    "Fields": "sample string 1",
    "Date": "sample string 2",
    "GenerateDate": true,
    "Limit": 4
  },
  "LookupTest": true
}
```
### Parameters

Name | Description
---- | -----------
Title | The title of the recipient. For example, `Mr`, `Mrs`, `Ms`, but not limited to anything
Firstname | The first name of the recipient
Lastname | The last name of the recipient 
MobileNumber | A valid mobile number for the recipient
EmailAddress | An optional email address for the recipient
User{n} | Ten optional user fields that can be used for anything. Up to 2014 characters in length.
When | A date and time that can be used to control when their invite is sent out if the recipient list is connected to a survey
LookupTest | A boolean value indicating whether the recipient's mobile number should be checked. If it is not a mobile number then it will be rejected and added to the error report.


### Duplication Testing
It is possible to stop duplicate recipients being added to a recipient list. The checks are done against the existing
list of recipients in the list and the new ones being added. The following describes the parameters that can be
supplied in the optional `Duplication` parameter.

#### Fields
A list of fields separated by a comma that refer to what should be checked for duplication. These can be any from the following list:

Name | Description
---- | -----------
tel | Mobile number
email | Email address
firstname | The first name of the recipient
lastname | The last name of the recipient
title | The title of the recipient
user{n} | the user fields from 1 to 10

These fields are used to look for existing recipients and if there is a match this will result in a duplcation error.

#### Date & Limit
The name of a field as listed in the `Fields` parameter that can be used to check against as a date.
The limit is the number of days that must be the difference between today and the date in the field before the recipient is not considered to be a duplicate.
This supports the idea of adding recipients only if they have not been contacted in the last so many days.

#### GenerateDate
A boolean value that indicates whether the `Date` field should be updated by this process when the recipient is successfully added.
This provides the ability for this process to maintain the Date field itself rather than you having to maintain it
in your data.


### Returns
If there were errors adding the recipients then a list of errors as an array of strings. For example:
```
{
  "Errors":["Error 1", "Error 2"]
}
```
If a lookup request was made then a list of these errors are also included.
If there are duplication errors then a list of recipients that are duplicated are returned.
If there was no problem then the following is returned:
```
{
  "Status": "Success"
}
```
If there is a problem with the mobile number then you can expect the following report format for each mobile number check:
```
There was a problem with the following recipient {Title} {FirstName} {LastName {EmailAddres} {MobileNumber} {ErrorMessage}
```
The current error message is `Invalid mobile number for`.


If there was a problem with the lookup of the mobile number then you can expect the following response for each lookup error:
```
{ "Carrier": "Carrier-Value", "Message": "Message", "Number": "Number", "Reachable":"Reachable" }
```

Name | Description
---- | -----------
Carrier | The name of the carrier. This can be any valid string or the word `Unknown`
Message | A status message which varies depending on the success of the lookup and the carrier involved.
Number | The number that was looked up
Reachable | A boolean value indicating whether the number is reachable.

### Statuses

Status | Description
------ | -----------
200 | Success
400 | Invalid Session. Please ensure you Login first
400 | No such list found
400 | There was a problem adding the recipients. Please contact OnePoint Global Support
