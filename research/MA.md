# Label: MA

## Description

Almost exclusively sent by the A350 - MIAM messages

In most cases, the final message is split across multiple messages and needs to be reassembled completely in orer to read the message

All messages seem to be within the bounds of T.0 and |
## Examples

Example 1 (from HL8079)
```
T.0&HDeF/kAYq0K2"hz7ck?4|
```

```
T.0&HDeF/kAYq0K2#kz#qb!E|
```

```
T.0&HDeF/kAYq0K2"VzflE(B|
```

## Acronyms / Codes

## Analysis

The garbled data is almost certainly compressed data. On the A350, deflate appears to be the algorithm used in all the examples I have seen.

Label H1 appears to indicate what the compression algorithm and encoding used for MIAM are and is sent almost immediately before the MA messages, though not all H1 messages contain the encoding and compression information.

libacars appears to have a decoder capable of (partially) reassembling and then decoding what has been reassembled.