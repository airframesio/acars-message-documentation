# Label: H1, Preamble: "FPN"

Flight Plan

## Format

The message begins with `FPN/` followed by a status. After that, it is a list of key/value pairs delimited by `:`. The final 4 characters are a checksum (algorithm unknown).

### Known Statuses

key | value
---|-----
RI | Route Inactive
FNXXXX | Flight Number XXXX

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

### First Waypoint
There can be multiple First Waypoints in a message. I believe they are related to the prior keypair. see [Landing](#landing)

### Waypoints format
The use of the waypoints is designated by the prior key/value pair. 
Waypoints can either be delimiated by `..`, `.` or `,`. The exact meaning is currently unclear. Current guess is as follows (with incorrect terminology)

key | value
---|-----
.. | FAA Waypoint
.  | Local
,  | lat/lon in millidegrees

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
Arrival Airport | KDWF
Current Route | EWRDFW01(17L)..SAAME.J6.HVQ.Q68.LITTR..MEEOW..FEWWW
Arrival Procedure | SEEVR4.FEWWW
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
Departure Airport | KSFO
Arrival Airport | KPHX
First Waypoint | KAYEX,N36292W120569..LOSHN,N35509W120000..BOILE,N34253W118016..BLH,N33358W114457
Checksum | DDFB

# Resources
* https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/20130085669
* https://aerowinx.com/board/index.php?topic=5578.0