---
layout: default
title: Getting Started
nav_order: 2
---
# Getting Started

> For more information visit the [main page](../README.md)

## 1. Get A DIY SMS Account
In order to use the API you will need a DIY SMS Account. You can register for this on the developers portal at https://diysms.onepointglobal.com.

## 2. Create a Key
The DIY SMS API uses [HMAC Security](Security.md). To use this you will need to create a Key. A Key consistts of two parts:

1. The `AppId` which appears in the authentication header.
1. The `Key` which is the hidden key used by your client and our API to encrypt and decrypt the authentication header.

For strict security conformity we only allow a key to last for 365 days. You will need to renew your key before this time to ensure your access to the API continues to function correctly.

You can create as many Keys as you require for different applications.

## 3. Add a Webhook
Webhooks are used for [Callbacks](Callback.md). You can define as many Webhooks as you require to handle different events in the platform. You can also define custom webhooks with many of the API methods.

## 4. Send a Message
You are now ready to use the [message API](Message.md) to send out an SMS.

You can use the Webhook feature in your account to review the callbacks you have set up and their success.

You can use the Message History to monitor inbound and outbound messages through your Account.

## 5. Set up an Organization
An organization is like an account, with the difference that you can share it with others in the OnePoint Global Platform. Use your own account as a test environment and an Organization as the live environment. Work with other team members to coordinate your efforts.

