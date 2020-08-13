# Survey

> For more information visit the [main page](../README.md)

The Survey API's allow you to get survey results and assess the status of a survey.

## GetResults
Get your survey results.
```
URL: base/Survey/GetResults
Method: POST
{
  "Format": "sample string 1",
  "Header": true,
  "Since": "2020-02-04T16:09:42.9927661+00:00",
  "SortOrder": 1,
  "SurveyReference": "sample string 2"
}
```
### Parameters

Name | Description
---- | -----------
Format | Describes the format in which the results should be supplied. See below for more details
Header | A boolean value that indicates whether a header row is supplied in the delimited type exports.
Since | Date and time indicating when the results should be checked from.
SortOrder | Each question is given a sort order from 1 onwards. This value indicates that this question must be answered, at least, for the results to appear in the export. This supports the idea of ensuring that if the first actual question requiring a response is the second question then this value could be 2 and the export results do not contain those where only an introduction was sent and the first question was not answered.
SurveyReference | The unique survey reference for the survey when it was set up.

### Format
The format parameter controls what format the data is returned in. It can be any one of the following:

Format | Description
------ | -----------
CSV | Comma delimited
PIPE | Pipe delimited
TAB | Tab delimited
XML | XML structured format
JSON | JSON structured format

### Returns
```
the survey results depending on the format requested.
```
### Statuses

Status | Description
------ | -----------
404 | Not Found
400 | There was a problem getting the results of the survey
404 | No results found since 2020-02-04T16:09:42.9927661+00:00

## GetSnapshot
Get a snapshot of specific question results
```
URL: base/Survey/GetSnapshot
Method: GET
{
  "SurveyReference": "sample string 1",
  "SortOrder": 2
}
```
### Returns
```
The snapshot of a question varies depending on the type of question.
```
### Statuses

Status | Description
------ | -----------
404 | This survey does not exist
400 | There was a problem processing the survey snapshot
400 | The survey has not yet shown any activity
400 | The sortOrder is out of range - it must be between 1 and the number of questions

### Status
Get the status of your survey.
```
URL: https://api.1pt.mobi/gateway/api/Survey/Status?surveyReference={surveyReference}
Method: POST
```
### Returns
```
{
   "Recipients": "recipientCount",
   "Anomalies": "anomalyCount",
   "Completed": "completionCount",
   "Started": "startedCount",
   "Delivered": "deliveredCount",
   "Abandoned": "abandonedCount",
   "Outstanding": "outstandingCount"
}
```
### Return Parameters

Name | Description
---- | -----------
Recipients | The number of recipients in the survey's recipient list.
Anomalies | The number of anomalies encountered in the survey.
Completed | The number of completed interviews in the survey.
Started | The number of started interviews in the survey.
Delivered | The number of invites delivered to recipients.
Abandoned | The number of abandoned interviews in the survey.
Outstanding | The number of interviews outstanding in the survey.

### Statuses

Status | Description
------ | -----------
404 | This survey does not exist
400 | The survey has not yet shown any activity
400 | The sortOrder is out of range - if must be between 1 and the number of questions


