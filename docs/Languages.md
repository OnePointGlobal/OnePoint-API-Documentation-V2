---
layout: default
title: Languages
parent: Messaging
nav_order: 3
---
# Languages

> For more information visit the [main page](../README.md)

SMS Supports all languages, but there are some important points that need to be understood:

## Character Sets
Whilst the OnePoint Global Platform will automatically handle any characters provided in a message you want to send out, you need to be aware that some messages can take up more space that you expect. Generally speaking there are three character sets to be aware of:

1. GSM
1. UTF8
1. UNICODE

## Keyword Management
OnePoint Global will automatically manage certain keywords, such as STOP. These keywords are generally detected in English, but in some countries we automatically detect other languages. For example, in France we support `arret`.

OnePoint Global Reserves the right to manage the keywords based on individual country requirements.
