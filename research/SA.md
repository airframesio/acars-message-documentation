# Label: SA

## Description

Media Advisory

## Examples

```
https://globe.adsbexchange.com/?icao=A94B4B&showTrace=2024-09-22&timestamp=1726969107
0E20138252

https://globe.adsbexchange.com/?icao=A86407&showTrace=2024-09-22&timestamp=1727016983
0LS221456V/

https://globe.adsbexchange.com/?icao=A3534A&showTrace=2024-09-22&timestamp=1727018138
0E21515382

https://globe.adsbexchange.com/?icao=A12FDA&showTrace=2024-09-22&timestamp=1727024327
0LS165850V

https://globe.adsbexchange.com/?icao=A12FDA&showTrace=2024-09-22&timestamp=1727024338
0LS165850V

https://globe.adsbexchange.com/?icao=A86407&showTrace=2024-09-22&timestamp=1727024652
0LS221704V/

https://globe.adsbexchange.com/?icao=A86407&showTrace=2024-09-22&timestamp=1727024671
0LS221704V/

https://globe.adsbexchange.com/?icao=A2FEE9&showTrace=2024-09-22&timestamp=1727037247
0E22034062S/

https://globe.adsbexchange.com/?icao=A23BFB&showTrace=2024-09-23&timestamp=1727100501
6EV140812V/

https://globe.adsbexchange.com/?icao=40683E&showTrace=2024-09-23&timestamp=1727104433
0LH151351VS

https://globe.adsbexchange.com/?icao=40683E&showTrace=2024-09-23&timestamp=1727104753
0LH151911VS

https://globe.adsbexchange.com/?icao=40641D&showTrace=2024-09-24&timestamp=1727220657
0LH233056VS

https://globe.adsbexchange.com/?icao=A19357&showTrace=2024-09-29&timestamp=1727652278
0EV232437V

https://globe.adsbexchange.com/?icao=A1C935&showTrace=2024-09-29&timestamp=1727653024
0EV233702V/

https://globe.adsbexchange.com/?icao=A5E02D&showTrace=2024-09-29&timestamp=1727653100
0EV233817V
```

## Acronyms / Codes

...

## Analysis

The first three characters vary but the purpose is unknown. The first is almost always a 0, though a 6 was observed once. The second is typically an E though L is somewhat common. If the second character is an L the third one is usually an S but sometimes an H. If the second character is an E then the third is usually a V but sometimes a 2.

The next 6 characters are the current time in UTC, HH:MM:SS.

After the time, there are a variable number of characters. All current examples are one of "V", "2", "VS", "V/", or "2S/".

V = VDL-M0/A (Plain Old ACARS)
2 = VDL-M2
S = SATCOM
H = HFDL
E = ?





