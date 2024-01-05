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

#### Waypoints format
The use of the waypoints is designated by the prior key/value pair. 
Waypoints can either be delimiated by `..`, `.` or `,`. The exact meaning is currently unclear. Current guess is as follows (with incorrect terminology)

key | value
---|-----
.. | FAA Waypoint
.  | Local
,  | position in millidegrees

To explain the position, N and E are positive while S and W are negative. the lat/lon are whole numbers in millidegrees meaning, you must divide by 1000 to get the lat/lon. Latitudes will always be 5 digits, while longitudes will always be 6. They will be zero padded to fit this length. As an example, `N01234W123456` translates to a position of `1.234,-123.456`.

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
Current Route | EWRDFW01(17L)..SAAME.J6.HVQ.Q68.LITTR..MEEOW..FEWWW
Arrival Procedure Name | SEEVR4.FEWWW
Arrival Waypoints | VECTOR..DISCO..RIVET
Approach Procedure | ILS 17L.RIVET
Approach Waypoints | TACKE
Checksum | C8B5


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
Arrival Procedure | EAGUL6.ZUN
Approach Procedure | ILS26..AIR,N40010W080490.J110.BOWRR..VLA,N39056W089097..STL,N38516W090289..GIBSN,N38430W092244..TYGER,N38410W094050..GCK,N37551W100435..DIXAN,N36169W105573..ZUN,N34579W109093
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
First Waypoint | KAYEX,N36292W120569..LOSHN,N35509W120000..BOILE,N34253W118016..BLH,N33358W114457
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

**Note:** First Waypoint can be parsed further, but the format is still being decoded


## Resources
* https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/20130085669
* https://aerowinx.com/board/index.php?topic=5578.0