# Label: H1, Preamble: "POS"

## Description

Observed on Alaska Airlines (AS) flights.

## Examples

Variant 1

### Example from flight AS0731, registration N841VA, ICAO AB856C (Alaska Airlines)
Recorded Wednesday, September 21, 2022 21:58:01 UTC

```
POSN43312W123174,EASON,215754,370,EBINY,220601,ELENN,M48,02216,185/TS215754,0921227A40
```

Flight was from Seattle, WA (SEA) to San Francisco, CA (SFO).

Variant 2

### Example from flight AS1138, registration N319AS, ICAO A36851 (Alaska Airlines)
Recorded Wednesday, September 21, 2022 22:03:10 UTC

```
POSN45209W122550,PEGTY,220309,134,MINNE,220424,HISKU,M6,060013,269,366,355K,292K,730A5B
```

In this variant, the 366 is the ground speed in knots.

Flight was from Portland, OR (PDX) to San Jose, CA (SJC).

Variant 3

### Example from flight AS0217, registration N639VA, ICAO A86107 (Alaska Airlines)
Recorded Wednesday, September 21, 2022 22:05:22 UTC

```
POSN43030W122406,IBALL,220516,380,AARON,220816,MOXEE,M47,0047,86/TS220516,092122BF64
```

Flight was from San Jose, CA (SJC) to Portland, OR (PDX).

Variant 4

### Example from flight UA2232, registration N36272, ICAO A41722 (United Airlines)
Recorded Wednesday, September 21, 2022 23:30:36 UTC

```
POSN33225W079428,SCOOB,232933,340,ENEME,235712,FETAL,M42,003051,15857F6
```

Flight was from Washington, DC (IAD) to Fort Lauderdale, FL (FLL).

## Acronyms / Codes

- N - Latitude North
- POS - Position
- TS - Time Stamp
- W - Longitude West
- P - Plus Celcius
- M - Minus Celcius

## Analysis

Comma separated list:
\<Position\>,\<Future WayPoint\>,\<Unknown\>,\<Altitude in hundreds\>,\<Future WayPoint\>,\<ETA over Future Waypoint\>,\<Future WayPoint\>,\<Outside Air Temperature\>,\<Unknown\>,\<ETA over Future Waypoint\>,\<Groundspeed or Date\>,\<Unknown\>,\<Unknown\>,\<Unknown\>

\<Position\> is POS\<Latitude Direction\>\<Latitude\*1000\>\<Longitude Direction\>\<Longitude\*1000\>

In variant 1 and 3, the next to last section includes the \<TimeStamp\>, \<Unknown\>/TS\<Hour\>\<Minute\>\<Second\>

In variant 1 and 3, the last section includes the \<Date\>, \<two digit month\>\<two digit day\>\<two digit year\>\<Unknown\>.

Outside air temperature is prefixed with an M when it is minus celcius, and P when it is positive celcius.
