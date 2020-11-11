---
layout: default
title: Stop Lists
parent: Messaging
nav_order: 2
---
# Stop Lists

> For more information visit the [main page](../README.md)

When a number responds to an SMS from OnePoint Global we look for a number of keywords and reply to them automatically in line with the countries standard requirements. These keywords are:

Keyword | Description
------- | -----------
STOP | A respondent usually replied to a message with STOP to indicate they no longer want any further messages from the number. Added to this we support the following associated keywords and phrases: STOP ALL, CANCEL,  END, UNSUBSCRIBE, QUIT. Added to that we also have [language support](Languages.md)
HELP | When a respondent is unsure as to what to do in some countries we have to respond to this keyword with a support message to contact us or use the STOP keyword.
INFO | Similar to the HELP keyword

## The Process
The STOP keyword triggers a special process within the OnePoint Global system that consists of the following steps:

1. The mobile number is placed on the OnePoint Global STOP List.
1. You are notified that this has taken place should you have a [Callback](Callbacks.md) set up.

> It is possible to opt out of OnePoint Globals STOP List management and refer all STOPS to your platform. By using your OnePoint Global Account you can confirm that you agree to supporting specific country regulations and we will pass all message back to your platform for management. Please note, at the same time we will be managing the numbers for our other clients, which will mean that they will be added to the relevant STOP lists.

### Unstopping
The recipient can cancel their entry in the stop list by replying with START, YES or UNSTOP.

### Campaign Stop Process
It is possible to set up keywords for that equate to STOP, HELP and INFO that you can associate with a campaign. This means that you can send an SMS with the following information:

```
Thank you for taking part in our survey. Reply CAMPAIGNSTOP to unsubscribe from this program, or STOP to cancel all messages from us.
```

Where the CAMPAIGN is used to distinguish between each STOP type keyword. For more information on setting up Keywords [click here](Keyword.md).

This will work for any number you are using shared or otherwise.

