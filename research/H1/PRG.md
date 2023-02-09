# Label: H1, Preamble: "PRG"

## Description

Observed on multiple Airbus A330 type aircraft. This appears to be a progress report showing the arrival runway and time.

## Examples

Variant 1

### Example from flight NW0163, registration N831NW, ICAO AB5D52 (Delta Airlines)
Recorded Thursday 09 February 2023 08:07:49.846 UTC

```
PRG/DTEHAM,18R,207,085235,041/FNDAL162/TS080747,090223AE30
```

Flight was from Minneapolis (KMSP) to Amsterdam (EHAM).

## Acronyms / Codes

- DT - Destination
- FN - Flight Number (although this is actually ATC callsign)
- N - Latitude North
- PRG - Progress
- TS - Time Stamp
- W - Longitude West

## Analysis
PRG/DT\<Arrival ICAO\>,\<Expected arrival runway entered in to FMGC\>,\<Possibly current fuel in LBS\>,\<unknown\>,\<Possibly fuel on landing in KGs\>/FN\<ATC Callsign\>/TS\<Time in hhmmss\>,\<Date in ddmmyy\>\<Checksum\>

The possible fuel elements are strange. I've used flight planning software designed for flight simulators to run some calculations and the numbers match up fairly well, just seems odd for one to be LBS and one to be KG!
