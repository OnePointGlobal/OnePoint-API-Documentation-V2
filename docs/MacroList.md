---
layout: default
title: Macro List
parent: Macros
nav_order: 1
---
# Macro Reference

> For more information visit the [main page](../README.md)

This section contains a full list of macros that can be used with the OnePoint Global API. Please check [here](Macros.md) for more information on how macros can be used.

## Messages
The following macros can be used when sending a message:

Name | Format | Description
---- | ------ | -----------
source | {source} | the source the message was sent from
destination | {destination}| the destinations the message will be sent to
brand | {brand(name)} | the branding to apply to the source if the network allows it
tiny | tiny(long,[tiny]) | the ability to turn a long url into a tiny url

## Recipients
The following macros can be used when sending a message that refers to a recipient:

Name | Format | Description
---- | ------ | -----------
first | {first} | the first name of a recipient
last | {last} | the last name of a recipient
telno | {telno} | the mobile number associated with the recipient

## Surveys
The following macros can be used when sending a message that is associated with a recipient within a survey. This includes all of the above macros in the recipients list and the following:

Name | Format | Description
---- | ------ | -----------
surveyname | {surveyname} | the name of the survey
surveydescritpion | {surveydescriptions} | the description of the survey
