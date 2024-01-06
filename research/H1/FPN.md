# Label: H1, Preamble: "FPN"

Flight Plan

## Format

Flight plan messages are variable length can be identified by beginning with `FPN/`. It can be described as a header, followed by N keypairs, ending with a checksum.

```
{header}:{key1}:{val1}:{key2}:{val2}:...:{keyN}:{valN}{checksum}
```

The key designates the type of data, where the value is the actual data. Each data type can have it's own format.

### Header
The header is a `/` delimited string in the format `{messageType}/{flightNumber}/{status}`. `messageType` is always `FPN` and {`flightNumber`} is optional. the Flight Number seems to only be set if the status is `RP`. As seen in the examples, headers will look like either `FPN/RI` or `FPN/FNAB1234/RP`.

#### Known Statuses

key | value
---|-----
RI | Route Inactive
RP | Route Planned

### Known Keys

key | value
---|-----
A  | Arrival Procedure
AA | Arrival Airport
AP | Approach Procedure (?)
CR | Current Route (?)
D  | Departure Procedure
DA | Departure Airport
F  | First Waypoint
R  | Departure Runway


#### First Waypoint
There can be multiple First Waypoints in a message. I believe they are related to the prior keypair. see [Landing](#landing)

#### Routes format
Routes are delimited by `.`. Routes will begin and end with either a position or waypoint. A waypoint can be annotated with a position using `,`. The format is `b{begin}.{airways}.{end}`. The airways is an optional field is also deliminated by `.` so you can go from airway to airway. This format can be repeated, where the end becomes the next beginning. For the examples. For purposes of explaining, i will annotate `..` as 'direct to' and `.` as 'along airway' with the exception of the last `.` being 'to' a waypoint.

Positions are coordinates in millidegrees. N and E are positive while S and W are negative. the lat/lon are whole numbers in millidegrees meaning, you must divide by 1000 to get the lat/lon. Latitudes will always be 5 digits, while longitudes will always be 6. They will be zero padded to fit this length. As an example, `N01234W123456` translates to a position of `1.234,-123.456`.

#### Procedures 
Procedures Look like they are in the format `{name}{route}` Where the route can be either a single waypoint or an entire route in the format described above


### Checksum
The last 4 characters of the message are a checksum. The algorithm is unkown

## Examples

### Landing
https://app.airframes.io/messages/2159379444

```
FPN/RI:DA:KEWR:AA:KDFW:CR:EWRDFW01(17L)..SAAME.J6.HVQ.Q68.LITTR..MEEOW..FEWWW:A:SEEVR4.FEWWW:F:VECTOR..DISCO..RIVET:AP:ILS 17L.RIVET:F:TACKEC8B5
```
means the following:

key | value
---|-----
Status | Route Inactive
Departure Airport | KEWR
Arrival Airport | KDFW
Current Route | From EWR to DFW take off runway 17 Left direct to SAAME along airway J6 along airway HVQ along airway Q68 to LITTR direct to MEEOW direct to FEWWW
Arrival Procedure Name | SEEVR4. initiate at FEWWW
Arrival Waypoints | VECTOR direct to DISCO direct RIVET
Approach Procedure | ILS for runway 17 Left. initiate at RIVET
Approach Waypoints | TACKE
Checksum | C8B5

*note - the `01` was dropped off as I believe it was just an identifier

### Full Flight
https://app.airframes.io/messages/2161768398

```
FPN/FNAAL1956/RP:DA:KPHL:AA:KPHX:CR:PHLPHX61:R:27L(26O):D:PHL3:A:EAGUL6.ZUN:AP:ILS26..AIR,N40010W080490.J110.BOWRR..VLA,N39056W089097..STL,N38516W090289..GIBSN,N38430W092244..TYGER,N38410W094050..GCK,N37551W100435..DIXAN,N36169W105573..ZUN,N34579W109093293B
``````


means the following:

key | value
---|-----
Flight Number | AAL1956
Status | Route Planned
Departure Airport | KPHL
Arrival Airport | KPHX
Current Route | PHLPHX61
Departure Runway| 27L(26O)
Departure Procedure | PHL3
Arrival Procedure | EAGUL6 initiate at ZUN
Approach Procedure | ILS26 direct to AIR,N40010W080490 along airway J110 along airway BOWRR direct to VLA,N39056W089097 direct to STL,N38516W090289 direct to GIBSN,N38430W092244 direct to TYGER,N38410W094050 direct to GCK,N37551W100435 direct to DIXAN,N36169W105573 direct to ZUN,N34579W109093
Checksum | 293B

### In-flight (?)
https://app.airframes.io/messages/2161761202

```
FPN/FNUAL1187/RP:DA:KSFO:AA:KPHX:F:KAYEX,N36292W120569..LOSHN,N35509W120000..BOILE,N34253W118016..BLH,N33358W114457DDFB
```

means the following:

key | value
---|-----
Flight Number | UAL1187
Status | Route Planned
Departure Airport | KSFO
Arrival Airport | KPHX
First Waypoint | KAYEX,N36292W120569 direct to LOSHN,N35509W120000 direct to BOILE,N34253W118016 direct to BLH,N33358W114457
Checksum | DDFB

## Parsing

To programatically parse, This is the procedure, I'd go with
1. strip off the checksum (last 4 chars)
    - bonus points: validate when algorithm is known
2. split by `:`
    - index 0 is the header
    - odd index is a key
    - even index is a value
3. parse the header
4. turn key/value pairs into a map
5. iterate and parse each pair accordingly


### Example

```
FPN/RI:DA:KMEM:AA:EGSS:F:HUMMS,N36214W088591..PXV,N37557W087457..ROD,N40173W084026..SLT,N41308W077582.J190..RKA,N42280W075144..MIILS,N46524W067029.N279A..TUDEP,N51100W053140..N52000W050000..N53000W040000..N54000W030000..N54000W020000..DOGAL,N54000W015000..BEXET,N54000W014000..BAKUR,N52145W005408.UN546..STU,N51597W005024.UP2..NUMPO,N51366W003170.Y3..BEDEK,N51223W001335CE78
```

First, strip off the checksum yielding

```
FPN/RI:DA:KMEM:AA:EGSS:F:HUMMS,N36214W088591..PXV,N37557W087457..ROD,N40173W084026..SLT,N41308W077582.J190..RKA,N42280W075144..MIILS,N46524W067029.N279A..TUDEP,N51100W053140..N52000W050000..N53000W040000..N54000W030000..N54000W020000..DOGAL,N54000W015000..BEXET,N54000W014000..BAKUR,N52145W005408.UN546..STU,N51597W005024.UP2..NUMPO,N51366W003170.Y3..BEDEK,N51223W001335
```

Splitting on `:` gives an array

```
['FPN/RI', 'DA', 'KMEM', 'AA', 'EGSS', 'F', 'HUMMS,N36214W088591..PXV,N37557W087457..ROD,N40173W084026..SLT,N41308W077582.J190..RKA,N42280W075144..MIILS,N46524W067029.N279A..TUDEP,N51100W053140..N52000W050000..N53000W040000..N54000W030000..N54000W020000..DOGAL,N54000W015000..BEXET,N54000W014000..BAKUR,N52145W005408.UN546..STU,N51597W005024.UP2..NUMPO,N51366W003170.Y3..BEDEK,N51223W001335']
```

We can pop off the header and parse `FPN/RI` as Flight Plan (we knew this) and `Route Inactive`

The remaining array, can be put into key pairs

```
[['DA', 'KMEM'], 
 ['AA', 'EGSS'],
 ['F', 'HUMMS,N36214W088591..PXV,N37557W087457..ROD,N40173W084026..SLT,N41308W077582.J190..RKA,N42280W075144..MIILS,N46524W067029.N279A..TUDEP,N51100W053140..N52000W050000..N53000W040000..N54000W030000..N54000W020000..DOGAL,N54000W015000..BEXET,N54000W014000..BAKUR,N52145W005408.UN546..STU,N51597W005024.UP2..NUMPO,N51366W003170.Y3..BEDEK,N51223W001335']
]
```

Then, iterate through the keys and parse accordingly.

key | value
---|-----
Status | Route Inactive
Departure Airport | KMEM
Arrival Airport | EGSS
First Waypoint | HUMMS,N36214W088591..PXV,N37557W087457..ROD,N40173W084026..SLT,N41308W077582.J190..RKA,N42280W075144..MIILS,N46524W067029.N279A..TUDEP,N51100W053140..N52000W050000..N53000W040000..N54000W030000..N54000W020000..DOGAL,N54000W015000..BEXET,N54000W014000..BAKUR,N52145W005408.UN546..STU,N51597W005024.UP2..NUMPO,N51366W003170.Y3..BEDEK,N51223W001335
Checksum | CE78

For the waypoints, we can replace `..` with ` direct to ` yielding the first waypoints as (with formatting)
```
HUMMS,N36214W088591 
direct to PXV,N37557W087457
direct to ROD,N40173W084026
direct to SLT,N41308W077582.J190
direct to RKA,N42280W075144
direct to MIILS,N46524W067029.N279A
direct to TUDEP,N51100W053140
direct to N52000W050000
direct to N53000W040000
direct to N54000W030000
direct to N54000W020000
direct to DOGAL,N54000W015000
direct to BEXET,N54000W014000 
direct to BAKUR,N52145W005408.UN546
direct to STU,N51597W005024.UP2
direct to NUMPO,N51366W003170.Y3
direct to BEDEK,N51223W001335
```

Then replace `.` with `along airway` or `to`
```
HUMMS,N36214W088591 
direct to PXV,N37557W087457
direct to ROD,N40173W084026
direct to SLT,N41308W077582 along airway J190
direct to RKA,N42280W075144
direct to MIILS,N46524W067029 along airway N279A
direct to TUDEP,N51100W053140
direct to N52000W050000
direct to N53000W040000
direct to N54000W030000
direct to N54000W020000
direct to DOGAL,N54000W015000
direct to BEXET,N54000W014000 
direct to BAKUR,N52145W005408 along airway UN546
direct to STU,N51597W005024 along airway UP2
direct to NUMPO,N51366W003170 along airway Y3
direct to BEDEK,N51223W001335
```

And for fun, let's turn the positions into something usable. 

```
HUMMS(36.214,-088.591) 
direct to PXV(37.557,-087.457)
direct to ROD(40.173W084026)
direct to SLT(41.308,-077582) along airway J190
direct to RKA(42.280,-075144)
direct to MIILS(46.524,-067029) along airway N279A
direct to TUDEP(51.100,-053140)
direct to 52.000,-050.000
direct to 53.000,-040.000
direct to 54.000,-030.000
direct to 54.000,-020.000
direct to DOGAL(54.000,-015.000)
direct to BEXET(540.00,-014.000)
direct to BAKUR(52.145,-005.408) along airway UN546
direct to STU(51.597,-005.024) along airway UP2
direct to NUMPO(51.366,-003.170) along airway Y3
direct to BEDEK(51.223,-001.335)
```

## Resources
* https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/20130085669
* https://aerowinx.com/board/index.php?topic=5578.0