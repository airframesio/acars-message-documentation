# Label: H1, Sublabel: DF

## Description

Data, Flight
This sublabel has been observed with American Airlines [AA], Southwest Airlines [WN],
and United Airlines [UA].
Examples from other carriers are solicited.

## Example 1 - Southwest Airlines N8713M

### raw
```
{
  "app": {
    "name": "dumpvdl2",
    "ver": "2.1.1"
  },
  "station": "FV-KDWH1-VDLM2",
  "t": {
    "sec": 1655533437,
    "usec": 203081
  },
  "freq": 136650000,
  "burst_len_octets": 254,
  "hdr_bits_fixed": 0,
  "octets_corrected_by_fec": 0,
  "idx": 0,
  "sig_level": -36.161083,
  "noise_level": -52.2617,
  "freq_skew": 2.698063,
  "avlc": {
    "src": {
      "addr": "ABFCDA",
      "type": "Aircraft",
      "status": "Airborne"
    },
    "dst": {
      "addr": "11517A",
      "type": "Ground station"
    },
    "cr": "Command",
    "frame_type": "I",
    "rseq": 0,
    "sseq": 0,
    "poll": false,
    "acars": {
      "err": false,
      "crc_ok": true,
      "more": true,
      "reg": ".N8713M",
      "mode": "2",
      "label": "H1",
      "blk_id": "1",
      "ack": "!",
      "flight": "WN0655",
      "msg_num": "D45",
      "msg_num_seq": "A",
      "sublabel": "DF",
      "msg_text": "++86501,N8713M,B7378MAX,220618,WN655 ,KOAK,KHOU,1175,SMX47-2102-0000\r\n6\r\nN2954.0,W09611.6,180618,14449, 00.5, 65,009,DC,
00000,0,\r\nN2953.2,W09605.2,180619,12625, 05.0,148,001,DC,00000,0,\r\nN2952.5,W09558.9,18"
    }
  }
}

```

### raw message text
```
++86501,N8713M,B7378MAX,220618,WN4406,KHOU,KOAK,1176,SMX47-2102-0000\r\n6\r\nN2940.2,W09539.7,181118,13159, 02.8,115,008,CL,00000,0,\r\nN2941.0,W09541.4,181118,13804, 01.0, 97,009,CL,00000,0,\r\nN2941.8,W09543.4,181119,14103, 00.5,117,011,CL,00000,0,\r\nN2942.4,W09545.5,181119,14385,-00.3, 91,011,CL,00000,0,\r\nN2942.9,W09547.8,181119,14707,-01.0, 97,014,CL,00000,0,\r\nN2943.5,W09550.1,181120,15382,-02.3, 99,011,CL,00000,0,\r\n:\r\n
```

### Formatted message text
```
++86501,N8713M,B7378MAX,220618,WN4406,KHOU,KOAK,1176,SMX47-2102-0000
6
N2940.2,W09539.7,181118,13159, 02.8,115,008,CL,00000,0,
N2941.0,W09541.4,181118,13804, 01.0, 97,009,CL,00000,0,
N2941.8,W09543.4,181119,14103, 00.5,117,011,CL,00000,0,
N2942.4,W09545.5,181119,14385,-00.3, 91,011,CL,00000,0,
N2942.9,W09547.8,181119,14707,-01.0, 97,014,CL,00000,0,
N2943.5,W09550.1,181120,15382,-02.3, 99,011,CL,00000,0,
:

```

## Analysis 1

### line 1

1. ++86501 - may indicate a version of the message.  See notes below.
2. N8713M - the registration number of the airframe
3. B7378MAX - airframe model
4. 220618 - two digits of year, month, day, in UTC
5. WN4406 - flight number
6. KHOU - departing airport
7. KOAK - destination airport
8. 1176 - not known
9. SMX47-2102-000 - not known

The first field seems to indicate a version of the message or perhaps the firmware providing
the message, as there are similar but not identical messages with different values that have
very similar data in lines 3 and subsequent.

An alternative hypothesis is that this field indicates which specific avionics subsystem is providing the data.

### line 2

6 - the number of lines of data following.

### line 3, which repeats the number of times specified in line 2

1. N2940.2 - latitude of data line
2. W09539.7 - longitude of data line
3. 181118 - time of data line, expressed as day of month, hour, and minutes, in UTC
4. 13159 - altitude of data line, in feet
5. 02.8 - not clear, speculate might be ambient air temperature, in Celsius
6. 115 - unknown
7. 008 - unknown
8. CL - unknown
9. 00000 - unknown
10. 0 - unknown

### last line

The last line is a colon (:).

## Example 2

### raw
```
7X400,7845,B737-700,220618,WN4140,KSAT,KBNA,0436,SW2103\r\n12.08.39,CR,1703,39002,243.3,.786,-54.2,-27.3,N2939.7,W09546.7,132120\r\n   0.67,FHP,AIR\r\n        1     2     3     4     5     6     7     8\r\nSIN,-0.78  0.29  0.26  0.29  0.29  0.25  0.31 -0.83\r\nSOU,-0.99  0.25  0.24  0.26  0.26  0.26  0.25 -1.15\r\nSRE,       0.62  0.61  0.62  0.62  0.62  0.62\r\nFEX, 0.34  0.32  0.32  0.32\r\nFRE,-1.97 -1.51 -1.28 -1.79\r\n
```

### Formatted
```
7X400,7845,B737-700,220618,WN4140,KSAT,KBNA,0436,SW2103
12.08.39,CR,1703,39002,243.3,.786,-54.2,-27.3,N2939.7,W09546.7,132120
   0.67,FHP,AIR
        1     2     3     4     5     6     7     8
SIN,-0.78  0.29  0.26  0.29  0.29  0.25  0.31 -0.83
SOU,-0.99  0.25  0.24  0.26  0.26  0.26  0.25 -1.15
SRE,       0.62  0.61  0.62  0.62  0.62  0.62
FEX, 0.34  0.32  0.32  0.32
FRE,-1.97 -1.51 -1.28 -1.79

```

## Analysis 2

### line 1

1. 7X400 - unknown, but see comments above
2. 7845 - alphabetic portion of airframe registration.  In this case, N7845A.
3. B737-700 - airframe model
4. 220618 - two digits of year, month, and day, in UTC
5. WN4140 - flight number
6. KSAT - departure airport
7. KBNA - destination airport
8. 0436 - unknown
9. SW2103 - unknown, but SW may refer to Southwest Airlines.



## Example 3, from flight AA1343, registration N902AA.

### raw
```
A321,022263,1,1,TB000000/REP291,00,00,4/\r\nTRP KDFW MMUN  7 8\r\n/A1 125440, 31.1365,- 96.7883,269,174.0,469,0.001790,\r\n0.000096,  9.67,- 52.66, 20.6,-26,10.19,0\r\n/A2 125740, 30.7472,- 96.7196,298,173.6,469,0.000814,\r\n0.000032, 15.78,- 69.17, 20.2,-33, 8.97,0\r\n/A3 130040, 30.4511,- 96.4142,310,173.3,466,0.000757,\r\n0.000024, 10.54,- 78.47, 19.9,-36, 8.50,0\r\n/A4 130340, 30.1588,- 96.1143,327,173.0,464,0.001138,\r\n0.000067, 12.52,-126.17, 19.6,-38, 7.83,0\r\n/A5 130640, 29.8711,- 95.8215,330,172.7,462,0.001394,\r\n0.000529, 10.98,-138.77, 19.3,-39, 7.74,0\r\n
```

### Formatted
```
A321,022263,1,1,TB000000/REP291,00,00,4/
TRP KDFW MMUN  7 8
/A1 125440, 31.1365,- 96.7883,269,174.0,469,0.001790,
0.000096,  9.67,- 52.66, 20.6,-26,10.19,0
/A2 125740, 30.7472,- 96.7196,298,173.6,469,0.000814,
0.000032, 15.78,- 69.17, 20.2,-33, 8.97,0
/A3 130040, 30.4511,- 96.4142,310,173.3,466,0.000757,
0.000024, 10.54,- 78.47, 19.9,-36, 8.50,0
/A4 130340, 30.1588,- 96.1143,327,173.0,464,0.001138,
0.000067, 12.52,-126.17, 19.6,-38, 7.83,0
/A5 130640, 29.8711,- 95.8215,330,172.7,462,0.001394,
0.000529, 10.98,-138.77, 19.3,-39, 7.74,0

```

Airframe is an Airbus A321.

## Analysis 3

### line 2

1. TRP - "trip"?
2. KDFW - departure airport
3. MMUN - destination airport
4. 7 - unknown
5. 8 - unknown

### line 3
Each data line is two actual lines, with a CRLF combination after the eigthth field.

1. /A1 - data line number
2. 125440 - time in UTC
3. 31.1365 - latitude, positive for north
4. \- 96.7883 - longitude, positive for east
5. 269 - unknown
6. 174.0 - unknown
7. 469 - unknown
8. 0.001790 - unknown

9. 0.000096 - unknown
10. 9.67 - unknown
11. \- 52.66 - unknown
12. 20.6 - unknown
13. -26 - unknown
14. 10.19 - unknown
15. 0 - unknown

## Example 4 from WN2377, registration N231WN

### raw

```
76401\r\n02E18KHOUKAUS\r\nN29711W09533517430434P018126005G859121::I8:9W\r\nN29744W09541617440731P013117004G810121::IPW/X\r\nN29779W09550317451089P006108008G782121::B0/9W\r\nN29819W09560717461392P000084009G788121::307GX\r\nN29860W09571817471764M006191003G742121::B0YY,\r\nN29881W09584117482022M009103010G6851210030W/X\r\n
```

## Example 5 from AM0472, registration XA-AMU

### raw

```
A01ACGHIJKXA-AMUN1MMMXKIAH5N107552W34379915338090638+137126006HE200Z:700004000000000000000U00001000
```

Flight was from MMMX (Mexico City) to KIAH.

## Example 6 from UA0614, registration N27253.

### raw 
```
ABS011DA_N27253  KIAHKSMF4\r\n 30018 -953982310000761+308125016XH08GX1151420000--\r\n 29930 -953620155001989+24-143014X1P/9W0661150000--\r\n 29907 -954310156004131+21-111011XZ:700++++++0000--\r\n 29918 -955200157006476+165 98011XZ:700++++++0000--\r\n 29942 -956100158008966+14-112010XZ:700++++++0000--\r\n 29967 -957060159010665+12- 98007XZ:700++++++0000--\r\n```

Flight was from KIAH to KSMF.
