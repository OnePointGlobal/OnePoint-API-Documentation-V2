---
layout: default
title: Message Windows
parent: Messaging
nav_order: 6
---
# Message Windows

> For more information visit the [main page](../README.md)

Message windows are used to control when a message can be sent from the OnePoint Global platform. It is based on the possibility that messages could be queued up in the platform (due to a heavy load) and they should not be sent out at inappropriate times. If a window is defined then the platform knows to hold on to the message if the associated window is closed.

A window is defined by three parameters:
1. From - a time when the window is open
1. To - a time when the window is closed
1. Days - the days the window is open

The times are based on UTC time.

## Adjusting for Country Time Zone
The OnePoint Global Platform will automatically adjust the time based on the destination country of the message to be sent. This means that a window of 9am to 4pm UTC will be altered by one hour if the message is to be sent to Germany, for example.

## Multiple Windows
It is also possible to define multiple windows to cater for different windows on different days. For example it may be necessary to have a different window during the week compared to the weekend.

For examples of how windows are used in sending messages check [here](Message.md).
