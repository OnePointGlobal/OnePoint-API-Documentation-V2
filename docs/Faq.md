---
layout: default
title: FAQ
nav_order: 3
---
# FAQ

> For more information visit the [main page](../README.md)

Here are some frequently answered questions for you:

## How do we manage multiple Tiny URLs in a single account?

The OnePoint Global Platform provides the ability to have multiple tiny URLs associated with a single account. These are maintained through your Administration account and can be used in the API. When you have multiple tiny URLs there will be a default URL you can choose that the API will pick automatically for you. If you want to use one of the other URLs you will need to specify it through the [Macro Parameters](Macros.md).

## Getting your Message Delivery Reports over the API

The [Callback](Callbacks.md) feature built into our API allows you to keep track of every message delivery in real time. For a full history you can access your OnePoint Global Account online to download bulk results.

## How is Callback failure handled?

If a callback to your platform fails we have an Exception Handling process. For more information please read the [Callbacks](Callbacks.md) documentation.

## Who handles STOP's in foreign languages?

The OnePoint Global Platform has STOP handling built in. OnePoint Global manages the list of words that are detected as STOP and a [callback](Callbacks.md) can be used to let you know that the STOP occurred. OnePoint Global has a [Global Stop List](Stop.md) that is managed on behalf of all of its clients to ensure that numbers are not contacted incorrectly and the ability to associate campaign keywords with the functionality of STOP, HELP and INFO.

## Who handles data destruction?

OnePoint Global has a [Data Protection Policy](http://resources.onepointglobal.com/data-protection/) that supports data destruction.

It is also possible to `kill` data associated with a specific mobile number that is also associated with your account. For more information [check here](Message.md).

Ultimately you may be interested in a custom Data Protection Policy. In this instance please contact our [Client Services Team](https://www.onepointglobal.com/open-account/).

