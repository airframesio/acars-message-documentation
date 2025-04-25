# Label: 2L, Preamble: DAT

## Description

Used by Jetstar (Australian airline) flights. Observed around YSSY by [s0's ACARS Hub](https://acars.s0.is/)

## Examples

#### 00:41Z: JQ952, at takeoff from SYD destination CNS. Departed gate 00:26Z

Message Label: 2L Unknown Message Label  
Non-Decoded Text:
```
DAT 16MAR25
UTC 0041
REG VHVGZ
FLT JST952
GWT 0
ZFW 602
FOB   120
CAP 160650
FO  611369
LOG 479189
LDR 0
DRT 0023
```
Tail: VH-VGZ Flight: JST0952/JQ0952 

#### 01:02Z: JQ840, at takeoff from SYD destination PPP, dep gate 00:42Z

Message Label: 2L Unknown Message Label  
Non-Decoded Text:
```
DAT 16MAR25
UTC 0102
REG VHVGN
FLT JST840
GWT 0
ZFW 572
FOB   138
CAP 137794
FO  692097
LOG 439365
LDR 0
DRT 0040
```
Tail: VH-VGN Flight: JST0840/JQ0840 

#### 01:14Z: JQ848, at takeoff from SYD destination HTI

Message Label: 2L Unknown Message Label  
Non-Decoded Text:
```
DAT 16MAR25
UTC 0114
REG VHVFX
FLT JST848
GWT 0
ZFW 588
FOB   107
CAP 167085
FO  692901
LOG 484212
LDR 0
DRT 0054
```
Tail: VH-VFX Flight: JST0848/JQ0848 


## Acronyms / Codes

| Code | Meaning | Format/Comment |
| - | - | - |
| DAT | UTC Date | [strftime:](https://strftime.org/)`%d%b%y` & `.upper()` |
| UTC | UTC Time | [strftime:](https://strftime.org/)`%H%M` |
| REG | Airframe registration |
| FLT | Flight number |
| GWT | Gross weight? So far normally `0` |
| ZFW | Zero-Fuel Weight | same unit as below? |
| FOB | Fuel On Board in unknown unit? | Typical A320 capacity is 27000L or 7000-ish Gallons. That's about 19t or 43000 lbs. Is this in hecto-kilograms?! |
| CAP | Captain ID number | Internal Jetstar ID? |
| FO  | First Officer ID number | " |
| LOG | Logistics? Logged hours? unsure. |
| LDR | Labor Distribution Reporting or Landing Distance Required | So far only observed as `0` |
| DRT | ? Appears to be just before aircraft departs the gate, perhaps a filing time? | Appears to be in `%H%M` format |

## Analysis

...
