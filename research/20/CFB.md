# Label: 20, Preamble: #CFB

### Examples

```
#CFB/1315//38//0//RA-1

TCAS//13DEC//1327//37//161//RA1 (1SA1) / TCAS (1SG)

VHF-3//13DEC//1327//52//158//VHF3

VIA-1//13DEC//1407//31985//282//DU-6 LOW BRIGHTNESS..
NO RA-1 DATA..

VIA-2//13DEC//1407/
```

```
#CFBWRN/WN19121418390034000006NAV TCAS FAULT
```

```
#CFBFLR/FR19121418400034433406TCAS (1SG)
/IDTCAS
,EIS 2
,ECAM 2
,EIS 1
,ECAM 1
,EIS 3
```

```
#CFBECT FAULT     CH-A

TCAS//15DEC//1253//76//168//RD2 (----) / TCAS (1SG)
RD1 (----) / TCAS (1SG)//TD2 (----) / TCAS (1SG)
TD1 (----) / TCAS (1SG)//ADIRU1 (1FP1) / TCAS..(1SG)

END OF RPT
```

```
#CFBMPF/               /AN.N660AW/FIAAL652    /DM191216175200/DAKPHX/DSKSMF/WN19121618120034000006NAV TCAS FAULT
/FR19121618130034430006TCAS (1SG)
/IDTCAS
,EIS 2
,ECAM 2
,EIS 1
,EIS
```

```
#CFB.1/FLR/FR1602082254 27513406ADR1 X2,ADR3X,ADR2X,,,,,SFCC1 (21CV)/SFCC2 (22CV),HARD
```

### Acronyms / Codes

Code  | Meaning
----- | ----
CFB | Crew Flight Bag
ECT |
FLR | Realtime Failure
FR  | Recorded Fault
MPF |
WRN | Warning

`CRZ` = `Cruise Performance Data`
`TKO` = `Takeoff Performance Data`

## Analysis

For preamble specific analysis, see the following documents.

Full Preamble | Description
------------- | -----------
[#CFB.01](CFB/CFB.01) | Failure/fault/warning
#CFBFLR | Realtime Failure
#CFBMPF |
#CFBWRN | Warning
