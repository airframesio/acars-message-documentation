# ACARS Message Documentation

Discoveries, documentation, and notes relating to decoding ACARS message text.

[![Contributors](https://img.shields.io/github/contributors/airframesio/acars-decoder-typescript)](https://github.com/airframesio/acars-message-documentation/graphs/contributors)
[![Activity](https://img.shields.io/github/commit-activity/m/airframesio/acars-decoder-typescript)](https://github.com/airframesio/acars-message-documentation/pulse)
[![Discord](https://img.shields.io/discord/1067697487927853077?logo=discord)](https://discord.gg/airframes)

## Purpose

The purpose of this repository is to document the discoveries and notes related to decoding ACARS message text payload in order to better organize and develop the ACARS Decoder libraries. All efforts here will directly benefit the [Airframes ACARS Decoder library](https://github.com/airframesio/acars-decoder-typescript).

## Research

A collaborative effort of analyzing and researching ACARS message algorithms and structures is ongoing. This section serves to link to primary/current initiatives. We welcome Pull Requests for anything ongoing here so that it can eventually be confirmed and moved into the documentation.

Label | Sublabel | Preambles | Description
----- | -------- | --------- | -----------
[:;](research/colon-semicolon.md) | | | Aircraft Transceiver Frequency Change
[_d](research/_d.md) | | | Transponder Pings / No-Ops
[10](research/10.md) | | | Unknown - free format?
[11](research/11.md) | | | Lots of formats
[12](research/12.md) | | [N ](research/12/N-space.md)
[13](research/13.md) | | | Arrival Gate request (including ETOA)
[14](research/14.md) | | | Unknown
[15](research/15.md) | | | Flight Status
[16](research/16.md) | | [N ](research/16/N-space.md) | Positional Data (Boeing)
[17](research/17.md) | | | METAR request?
[18](research/18.md) | | | Unknown
[19](research/19.md) | | | Unknown
[1A](research/1A.md) | | | Unknown
[1B](research/1B.md) | | | Unknown
[1C](research/1C.md) | | | Unknown
[1D](research/1D.md) | | | Unknown
[1E](research/1E.md) | | | Unknown
1F
[1G](research/1G.md) | | | Unknown
1H
1I
1J
1K
[1L](research/1L.md) | | | Unknown
[1M](research/1M.md) | | | Unknown
1N
1O
[1P](research/1P.md) | | | Unknown
[1Q](research/1Q.md) | | | Unknown
[1R](research/1R.md) | | | Unknown
[1S](research/1S.md) | | | Unknown
[1T](research/1T.md) | | | Unknown
[1U](research/1U.md) | | | Unknown
[1V](research/1V.md) | | | Unknown
[1W](research/1W.md) | | | Unknown
[1X](research/1X.md) | | | Unknown
[1Y](research/1Y.md) | | | Unknown
[1Z](research/1Z.md) | | | Unknown
[20](research/20.md) | | [POS](research/20/POS.md)
[21](research/21.md) | | | Position
[22](research/22.md) | | | Position, time and altitude
[23](research/23.md) | | | Brake Release?
[24](research/24.md) | | | Unknown
[25](research/25.md) | | | Unknown
[26](research/26.md) | | | ETA, wind speed/direction and lat/lon
[27](research/27.md) | | | ETA, wind speed/direction and lat/lon
[28](research/28.md) | | | Unknown
[29](research/29.md) | | | Unknown
[2A](research/2A.md) | | | Unknown
[2B](research/2B.md) | | | Unknown
[2C](research/2C.md) | | | Unknown
[2D](research/2D.md) | | | Unknown
[2E](research/2E.md) | | | Unknown
[2F](research/2F.md) | | | Unknown
[2G](research/2G.md) | | | Unknown
[2H](research/2H.md) | | | Unknown
[2I](research/2I.md) | | | Unknown
[2J](research/2J.md) | | | Unknown
[2K](research/2K.md) | | | Unknown
[2L](research/2L.md) | | [DAT](research/2L/DAT-Jetstar.md) | Used by Jetstar AU for OOOI
[2M](research/2M.md) | | | Problem Report?
[2N](research/2N.md) | | | Unknown
[2O](research/2O.md) | | | Unknown
[2P](research/2P.md) | | | Unknown
[2Q](research/2Q.md) | | | Unknown
[2R](research/2R.md) | | | Reset
[2S](research/2S.md) | | | Unknown
[2T](research/2T.md) | | | Unknown
[2U](research/2U.md) | | | Final Loadsheet
[2V](research/2V.md) | | | Unknown
[2W](research/2W.md) | | | Unknown
[2X](research/2X.md) | | | Unknown
[2Y](research/2Y.md) | | | Unknown
[2Z](research/2Z.md) | | | Unknown
[30](research/30.md) | | [/EA](research/30/forward-slash-EA.md)
[31](research/31.md)
[32](research/32.md)
[33](research/33.md)
[34](research/34.md)
[35](research/35.md)
[36](research/36.md)
[37](research/37.md)
[38](research/38.md)
[39](research/39.md)
[3A](research/3A.md)
[3B](research/3B.md)
[3C](research/3C.md)
3D
[3E](research/3E.md)
[3F](research/3F.md)
[3G](research/3G.md)
[3H](research/3H.md)
[3I](research/3I.md)
[3J](research/3J.md)
[3K](research/3K.md)
[3L](research/3L.md)
[3M](research/3M.md)
[3N](research/3N.md)
3O
[3P](research/3P.md)
3Q
[3R](research/3R.md)
[3S](research/3S.md)
[3T](research/3T.md)
[3U](research/3U.md)
[3V](research/3V.md)
[3W](research/3W.md)
3X
3Y
[3Z](research/3Z.md)
4~
[40](research/40.md)| | | Ground to Air, Request for Clearance via Free Text w ATC, OPS and administrative msg/requests from ground, weather info.
41
42
43
44 | | | OOOI + Positions
45
46
47
48
49
[4A](research/4A.md)
4C
4E
4H
[4J](research/4J.md)| | | Position and weather
4K
[4L](research/4L.md)
4M
[4N](research/4N.md)
[4P](research/4P.md)
4Q
4R
4S
4T
4X
4Y
4Z
52
58
5D
5P
[5U](research/5U.md)
5V
5Y
[5Z](research/5Z.md) | | [/](research/5Z/forward-slash.md)
[80](research/80.md)
81
82
[83](research/83.md)
84
85
86
87
88
8A
8D
8E
8S
8X
99
A0
[A1](research/A1.md)
A2
[A3](research/A3.md)
A4
A6
A9
AA
[B0](research/B0.md)
[B1](research/B1.md)
[B2](research/B2.md)
[B3](research/B3.md)
[B4](research/B4.md)
[B5](research/B5.md)
[B6](research/B6.md) | | [/](research/B6/forward-slash.md)
[B9](research/B9.md) | | [/](research/B9/forward-slash.md)
[BA](research/BA.md)
BB
C1
CA
[H1](research/H1.md) | | [#CFB](research/H1/CFB.md), [#CFB.01](research/H1/CFB/CFB.01.md), [FPN](research/H1/FPN.md), [POS](research/H1/POS.md), [Qantas various](research/H1/Qantas.md) | Message to/from Terminal
[H2](research/H2.md)
[HX](research/HX.md)
[MA](research/MA.md) | | | Media Advisories (appears to be MIAM focused)
[Q0](research/Q0.md)
[Q2](research/Q2.md)
Q3
Q5
Q6
Q7
QA
QC
QD
QE
[QF](research/QF.md)
QP
[QQ](research/QQ.md)
QR
QS
QX
[RA](research/RA.md) | | |
[RB](research/RB.md)
RF
[SA](research/SA.md)
SQ | | | Squitters / Transponder Pings
VA
X1

## Documentation

We will compile and create actual documentation as we confirm our research results.

PENDING...

## Contributors

Name | Description
---- | -----------
[Kevin Elliott](https://github.com/kevinelliott) | Primary Airframes contributor
[Frank Vance / fvance](https://github.com/fvance) | Multiple label research contributions
[Andy / andermatt64](https://github.com/andermatt64) | Multiple label research contributions
[Thomas / period](https://github.com/period) | Multiple label research contributions
[Michael Johnson / johnsom](https://github.com/johnsom) | Multiple label research contributions
[Chris Globe / chrisglobe](https://github.com/chrisglobe) | Multiple label research contributions
[ge0metrix](https://github.com/ge0metrix) | Label updates
[Poggs](https://github.com/poggs) | Index fixes and label research
Unnamed | Several contributors who wished to be unnamed or I have not yet been granted permission to list here
