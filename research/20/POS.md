# Label: 20, Preamble: POS

## Description

Position report.

## Examples

### Type 1

```
POSN38160W077075,,211733,360,OTT,212041,,N42,19689,40,544
```

```
POSN37150W076112,,212053,360,,000534,,N45,184100,,360
```

```
POSN36160W076283,,213052,360,,005815,,N44,20092,,368
```

```
POSN34134W076563,,215052,360,,003641,,N43,22187,,381
```

```
POSN44132E021092,,081648,253,NISVA    ,001653,,N37,21747,61,368
```

### Type 2

```
POSN32249E045047,,082806,380,DEBNI
```

### Type 3
```
POS,,,,,,,,,,
```

## Acronyms / Codes


## Analysis

### Decoding Example 1

#### 1) Strip Preamble

```
POSN38160W077075,,211733,360,OTT,212041,,N42,19689,40,544
```

becomes

```
N38160W077075,,211733,360,OTT,212041,,N42,19689,40,544
```

#### 2) Split by comma (`,`) to get fields

Field | Value | Purpose
----- | ----- | ----
1 | N38160W077075 | Coordinates / Position
2 | |
3 | 211733 | Current time (UTC)
4 | 360 | Flight level
5 | OTT | Waypoint/Fix?
6 | 212041 | ETA to Waypoint (UTC)
7 | |
8 | N42 |
9 | 19689 |
10 | 40 |
11 | 544 |

#### 3) Parse/format field values

##### 3a) Coordinates / Position

Start | End | Count | Attribute | Raw Value | Formatted | Description
----- | --- | ----- | --------- | --------- | --------- | -----------
1 | 2 | 1 | latitude_direction | `N` | `N` | Latitude Direction (`N` or `S`)
2 | 7 | 5 | latitude | `38160` | `38.160` | Latitude
7 | 8 | 1 | longitude_direction | `W` | `W` | Longitude Direction (`W` or `E`)
8 | 14 | 6 | longitude | `077075` | `-77.075` | Longitude




### Decoding Example 2

#### 1) Strip Preamble

```
POSN32249E045047,,082806,380,DEBNI
```

becomes

```
N32249E045047,,082806,380,DEBNI
```

#### 2) Split by comma (`,`) to get fields

Field | Value | Purpose
----- | ----- | ----
1 | N32249E045047 | Coordinates / Position
2 | |
3 | 082806 | Current time (UTC)
4 | 380 | Flight level
5 | DEBNI | Waypoint/Fix?

#### 3) Parse/format field values

##### 3a) Coordinates / Position

Start | End | Count | Attribute | Raw Value | Formatted | Description
----- | --- | ----- | --------- | --------- | --------- | -----------
1 | 2 | 1 | latitude_direction | `N` | `N` | Latitude Direction (`N` or `S`)
2 | 7 | 5 | latitude | `32249` | `32.249` | Latitude
7 | 8 | 1 | longitude_direction | `E` | `E` | Longitude Direction (`W` or `E`)
8 | 14 | 6 | longitude | `045047` | `45.047` | Longitude
