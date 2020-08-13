# TinyUrl

> For more information visit the [main page](../README.md)

The TinyUrl API's allow you to generate tiny URL's for your SMS messages.

## Custom Tiny URL's
OnePoint supports custom Tiny URL's for each user of the API. It is possible for you to use the standard OnePoint Tiny URL (`1pt.mobi`) or for us to register a domain and set this
up for your account. For more information on this please contact us directly.

We also allow you to specify the tiny url as part of the call. In this instance you will responsible for ensure it has been successfully mapped with the OnePoint Global Platform.

## Metadata
It is possible associate meta data at the same time as registering the tinyurl so that it can be provided in any [callback](Callbacks.md).

## Register
Register a URL in return for a tiny URL.
```
URL: base/TinyUrl/Register
Method: POST
{
  "FullUrl": "http://onepointglobal.com",
  "TinyUrl": "https://1pt.mobi",
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
### Returns
```
{ "http://1pt.mobi/23423" }
```
### Statuses

Status | Description
------ | -----------
400 | There was a problem registering the tiny url

## RegisterList
Register a list of URL's in return for a list of tiny URL's
```
URL: base/TinyUrl/RegisterList
Method: POST
{
  "UrlList": [
    {
      "FullUrl": "https://www.onepointglobal.com"
      "TinyUrl": "https://1pt.mobi"
    },
    {
      "FullUrl": "https://www.google.co.uk"
      "TinyUrl": "https://1pt.mobi",
      "MetaData": 
      [
        { "RequestID": "1234567890DEFED" },
        { "OrgID": 1010 },
        { "Instance": "ETRERT"},
        { "Campaign": 1242 },
        { "TimeStamp": "2020-02-04T11:47:33.645773+00:00" }
      ]
    }
  ]
}
```
### Returns
```
{
  "UrlList": [ "tinyUrl1", "tinyUrl2" ]
}
```
### Statuses

Status | Description
------ | -----------
400 | There was a problem registering the tiny url

