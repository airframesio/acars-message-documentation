# Label: H1, Preamble: #CFB.01

### Examples

Item 1
```
#CFB.1/FLR/FR1602082254 27513406ADR1 X2,ADR3X,ADR2X,,,,,SFCC1 (21CV)/SFCC2 (22CV),HARD
```

### Acronyms / Codes

Code  | Meaning
----- | ----
CFB | Crew Flight Bag
FLR | Realtime Failure
FR  | Recorded Fault

Flight Phase | Meaning
----- | ----
`02` | Engine start + 3 mn up to TO Power
`03` | TO Power up to 80 kts
`04` | 80 kts up to lift off
`05` | Climb
`06` | Cruise
`07` | Descent
`08` | Touch down up to 80 kts
`09` | 80 kts up to last engine shut down

## Analysis

### Item 1

#### Message
```
#CFB.1/FLR/FR1602082254 27513406ADR1  X2,ADR3X,ADR2X,,,,,SFCC1 (21CV)/SFCC2 (22CV),HARD
```

This message is a realtime failure.

#### Parts

Parts derived by splitting on `/` twice into 3 parts (allowing for more slashes in the content without parsing now).

Part | Content | Purpose
---- | ------- | -------
1 | #CFB.1 | Preamble indicating Crew Flight Bag message
2 | FLR | Type / Category indicating Realtime Failure
3 | FR1602082254 27513406ADR1  X2,ADR3X,ADR2X,,,,,SFCC1 (21CV)/SFCC2 (22CV),HARD | Failure content

#### Chunks for Realtime Fault `Content`

Chunks derived by taking specified digits, then remainder as subcontent.

Chunk | Start Digit | Length | Field | Content | Parsed
----- | ----------- | ------ | ----- | ------- | ------
1 | 0 | 2 | Fault Record | `FR` |
2 | 2 | 6 | Date | `160208` | `2016-02-08`
3 | 8 | 4 | Time | `2254` | `22:54` or `10:54 PM`
4 | 12 | 1 | Empty space | ` ` |
5 | 13 | 6 | ATA SUBATA | `275134` |
6 | 19 | 2 | Flight Phase | `06` |
7 | 21 | 7 | `ADR1  ` | Source System
8 | 28 | Remainder | `X2,ADR3X,ADR2X,,,,,SFCC1 (21CV)/SFCC2 (22CV),HARD`

Remainder is split by commas to get the remainder chunks.

Chunk | Field | Content
----- | ----- | -------
1 | Fault classification | `X2`
2 | System Impacted | `ADR3X`
3 | System Impacted | `ADR2X`
4 | System Impacted |
5 | System Impacted |
6 | System Impacted |
7 | System Impacted |
8 | Fault Code or Detail | `SFCC1 (21CV)/SFCC2 (22CV)`
9 | Severity | `HARD` (or `INTERMITTENT`)
