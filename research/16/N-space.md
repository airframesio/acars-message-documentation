# Label: 16, Preamble: "N "

## Description

Observed on Alaska Airlines (AS) and AeroMexico (AM) flights.

## Examples

Variant 1

### Example from flight AS0015, registration N930VA, ICAO ACE785 (Alaska Airlines)
Recorded Sunday, September 18, 2022 23:29:37 UTC

```
N 44.203,W 86.546,31965,6, 290
```

Flight was from Santa Ana, CA (SNA) to Seattle, WA (SEA).

Variant 2

### Example from flight AS0192, registration N926VA, ICAO ACD650 (Alaska Airlines)
Recorded Sunday, September 18, 2022 23:35:54 UTC

```
N 42.777,W 85.477,35004,6, 132
```

Flight was from San Francisco, CA (SFO) to New York, NY (JFK).

Variant 3

### Example from flight AM0687, registration XA-DRA, ICAO 0D0B66 (AeroMexico)
Recorded Sunday, September 18, 2022 23:20:29 UTC

```
N 28.177/W 96.055
```

Flight was from Chicago, IL (ORD) to Mexico City, Mexico (MEX).


## Acronyms / Codes

- N - Latitude North
- W - Longitude West

## Analysis

In the case of the Alaskan Airlines messages, it is a comma separated list of
five items: Latitude, Longitude, Altitude, \<unknown\>, \<unknown\>

In the AeroMexico variant, it is a simple Latitude and Longitude, separated
by a forward slash.
