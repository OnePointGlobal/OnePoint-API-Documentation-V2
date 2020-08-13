# Message Statuses
Message Statuses are provided at different times in a messages journey to the destination:
1. The initial send to carrier provides a basic status.
1. Whilst the message is in transit through the carrier networks.
1. When the message arrives at the destination.

At any point in the journey a receipt with a status can be received. It is possible to receive multiple receipts for the same message whilst it is on its journey.

The following is a list of the possible statuses:

Status | Description
------ | -----------
Received | Received by OnePoint Global to process. This will mean that it has not yet bee processed either because OnePoint Global is waiting for the carrier to respond or the Windows and When parameters provided do not allow the message to be sent yet.
Sent | The message was sent to the carrier.
Timedout | The message was sent but there was no reply based on the timeout value.
Delivered | The message was successfully delivered to the destination.
Blocked | The destination was blocked by the carrier.
Blacklisted | The destination was black listed by the carrier. The distinction between this and block is not always made clear between carriers.
Failed | There was a problem submitting to the carrier. This covers all other potential issues with the carrier.
LandlineUnknown | This number is associated with a landline. It is possible to check the destination before the message is sent and this status indicated that the message was destined for a landline as therefore was not sent.
NoRoute | OnePoint Global is unable to find a suitable route for this message to be sent. In this case you should contact OnePoint Global Support.

> For more information about sending messages check [here](Message.md).

