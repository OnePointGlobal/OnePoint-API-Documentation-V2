---
layout: default
title: Macros
nav_order: 5
has_children: true
---
# Macros

> For more information visit the [main page](../README.md)

OnePoint Global support the principle ability to insert values into a message. This is achieved through its Macro Capability. Macros can be used during the recipient upload process and the Messaging process.

## Formatting Macros
Macros take the basic format as follows:

```
'{' name [ '(' parameters ')' ] '}'
```

Name | Description
---- | -----------
name | The name of the macro
parameters | an optional set of parameters depending on the type of macro

An example of a macro is the `tiny`, which takes the basic format:

```
{tiny(https://onepointglobal.com)}
```
The above macro will convert the long URL provided into a short version and based on your account settings will use either the default tiny URL or a specific one associated with your account.

## Parameters
Parameters have to be separated by commas. If a parameter includes a parameter then it needs to be surrounded by double quotes (`"`). For example:

```
{tiny(https://onepointglobal.com, 1pt.mobi)}
```
The above macro will convert the long URL into a tiny URL using the domain name provided as the second parameter as the tiny URL.

In the above examples the parameters are literal entries in message. It is also possible to refer to external references by using reference macros. For example it is possible to refer to values provided along with the method call when sending a message:

```
{tiny({long}, {short})}
```
In this example the `{long}` and `{short}` references must be included in the method to send a message. For example:

```
URL: base/Message/Send
Method: POST
{
  "Source": "OnePoint",
  "Destination": "12345678901",
  "Message": "Please click on the link {tinyurl({long}, {short})} to get your reward",
  "Reply": false,
  "When": "2020-02-04T11:47:33.645773+00:00",
  "Window": [{ From: "09:00", To: "16:00", Days: "1,2,3,4,5"}],
  "Callback": "https://yourco.com/api/messagetracker",
  "Lookup": true,
  "Test": false,
  "Macros":
    [
        { "long" : "https://onepointglobal.com" },
        { "short" : "1pt.mobi" }
    ]
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

> If there is a conflict with the macro list supplied in the API call and the standard macros the macro list takes precedence.

## Using the MetaData
In the same way the Macros can be used from the API call it is also possible to use the MetaData entries. This saves on duplication of entries. Using the above example the following macro formation could be used:

```
{tiny({long}/{RequestID}, {short})}
```

For a full list of macros please check [here](MacroList.md).



