Sublabel: EFFDE

Description

Existing Fault Flight Deck Effect Report (BOEING)
...

Examples

```
EFFDE 1 27FEB26 1031 AIVT-ALP AIC186D CYVR/LOWW 311B-BCG-00W-19 L
FDE 21200100 A
MSG 2124400 L
DB CABIN TEMPERATURE CONTROLLER (R CHAN2)
DB CABIN TEMPERATURE CONTROLLER (R CHAN1)
NCMM
MSG 4517100 A
DB CENTRAL MAINTENANCE COMPUTING FUNCTION
MSG 3140202 A
DB ACMF IN RIGHT AIMS
MSG 2359905 A
DB HF COMMUNICATION TRANSCEIVER (RIGHT)
EOR
```
...

Analysis

```
EFFDE = Existing Fault Flight Deck Effect Report
27FEB26 = DDMMYY Date
1031 = HHMM Time
AI = Aircraft Identification
VT-ALP = Aircraft Registration
AIC186D = Flight Number
CYVR = Departure Airport
LOWW = Destination Airport
311B-BCG-00W-19 = CMC Part Number
L = Left CMC (Source)
CMC = Central Maintenance Computer

FDE = Flight Deck Effect (STATUS message displayed on EICAS for FLT CREW attention)
21200100 = Fault Code
A or L = Active or Latched Fault
MSG = Message (Followed by Maintenance Message Number, example MSG 2124400)
DB = Detected By (Source System that detected the Fault)

NCMM = Non-Correlated Maintenance Message part of Report follows (with no STATUS related messages, for Maintenance Personnel only)

EOR = End Of Report
```
...




