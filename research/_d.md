# Label: _d

## Description

Frame acknowledgement 

## Examples

There is no content in the text field for these messages.

## Acronyms / Codes

None.

## Analysis

These frames are used to acknowledge the receipt of a previous frame from either the aircraft or ground station. The `ack` field specifies the t-be-acknowledged frame's `blk_id`. If an acknowledgement is not received by the other party, the originator will send a duplicate after a timeout interval. The timeout interval has not yet been determined. We are not sure if there is any value to us aside from DXing. 
