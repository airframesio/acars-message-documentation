# Label: HX

## Description

Undelivered Uplink Report

## Examples

### Prefix "RA FMT LOCATION"

```
https://globe.adsbexchange.com/?icao=A41722&showTrace=2024-09-24&timestamp=1727202494
RA FMT LOCATION N4009.6 W07540.8
```

* "RA FMT LOCATION "
* Latitude: "N" or "S" then 2 digits for degrees, then 3 digits with a decimal point for minutes
* Longitude: "W" or "E" then 3 digits for degrees, then 3 digits with a decimal point for minutes

### Prefix "RA FMT 43"

```
https://globe.adsbexchange.com/?icao=A92EA0&showTrace=2024-09-22&timestamp=1727038330
RA FMT 43 GSP B02

https://globe.adsbexchange.com/?icao=A14C70&showTrace=2024-09-23&timestamp=1727055864
RA FMT 43 BUF 20

https://globe.adsbexchange.com/?icao=A15027&showTrace=2024-09-24&timestamp=1727208254
RA FMT 43 IAD B72

https://globe.adsbexchange.com/?icao=A15795&showTrace=2024-09-25&timestamp=1727270461
RA FMT 43 SYR 25

https://globe.adsbexchange.com/?icao=A7D725&showTrace=2024-09-25&timestamp=1727273865
RA FMT 43 GSP B03

https://globe.adsbexchange.com/?icao=A37E80&showTrace=2024-09-25&timestamp=1727275831
RA FMT 43 CVG B25
```

* "RA FMT 43 "
* 3 character destination airport code
* 2 or 3 unknown characters

### More Examples

```
https://globe.adsbexchange.com/?icao=AB97E6&showTrace=2024-09-22&timestamp=1727015984
RA IV3 QUNDCULUA~1HOWGOZIT** PART 01 OF 01 **HOWGOZIT 2723-22 LGACI: 18        RLS: 02 LGA 1405/1429     243ALANNA    1441 26  218PTW      1446 2

https://globe.adsbexchange.com/?icao=AB97E6&showTrace=2024-09-22&timestamp=1727016010
RA FMT   209EMI      1457 26  204CSN      1506 26  195FANPO    1509 26  192MAULS    1518 26  184FEEDS    1528 36  175YICUT    1534 36  166ALEAN

https://globe.adsbexchange.com/?icao=A6BF4E&showTrace=2024-09-23&timestamp=1727060419
33 CRC FLT NO     LDW      TIME5135       64.3    0258ZWIND      OAT C      QNH024/05      13     30.12------------------------     REMAR

https://globe.adsbexchange.com/?icao=A6BF4E&showTrace=2024-09-23&timestamp=1727060425
33 CRC 7D3B

https://globe.adsbexchange.com/?icao=A57F04&showTrace=2024-09-23&timestamp=1727094488
/HDQDLUA.H1 MBB REQPOS037

https://globe.adsbexchange.com/?icao=A00DF9&showTrace=2024-09-24&timestamp=1727146855
/ATSAAXA.C1 ??? .ATSAAXA 240300AGMAN N102UW-  ALB ATIS INFO T 0251Z.14003KT 10SM FEW044SCT050 BKN130 15/09

https://globe.adsbexchange.com/?icao=C05BC8&showTrace=2024-09-24&timestamp=1727179567
4P     0/96 A/C       TURN FM 1706/23SEP TA 12:20*          TURN TO 1605/24SEP TA 01:32***ALL TIMES ABOVE ARE UTC***

https://globe.adsbexchange.com/?icao=AA5B92&showTrace=2024-09-24&timestamp=1727203000
- #T19999AAFLT 0733 ARR CLT   ARR D5X BAG CUST 

https://globe.adsbexchange.com/?icao=AB6851&showTrace=2024-09-26&timestamp=1727354233
H1 MBB /AA USADCXA.AT1.N834MH21B25068403F44
```

## Acronyms / Codes

...

## Analysis

Formats are quite varied. First two characters are sometimes a valid ACARS message type label, but sometimes not. Even when it is, it often seems unrelated.
