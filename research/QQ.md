# Label: QQ

## Description

OFF Report

## Examples 

### With Position

```
https://globe.adsbexchange.com/?icao=A69423&showTrace=2024-09-23&timestamp=1727105501
KTEBKJYO1528001FE23152852N4052.1W07403.0014195    

https://globe.adsbexchange.com/?icao=AAC338&showTrace=2024-09-27&timestamp=1727472266
KMMUKCLT2124001FE27212415N4049.2W07423.50141940067
```

* 4 character origin airport code
* 4 character destination airport code
* 4 characters for current time in UTC, HH:MM
* "001FE"
* Day of month
* Current UTC time, HH:MM:SS
* Latitude: "N" or "S" then 2 digits for degrees, then 3 digits with a decimal point for minutes
* Longitude: "W" or "E" then 3 digits for degrees, then 3 digits with a decimal point for minutes
* A variable number of unknown characters

### Without Position

```
https://globe.adsbexchange.com/?icao=4D0214&showTrace=2024-09-22&timestamp=1727035501
KEWRKSWF20041942

https://globe.adsbexchange.com/?icao=ACB470&showTrace=2024-09-24&timestamp=1727202601
KEWRKDFW1829OS KDFW /FUL0306/MO 1816/APH 0000000

https://globe.adsbexchange.com/?icao=A2BD72&showTrace=2024-09-28&timestamp=1727539108
KEWRKBED15581531

https://globe.adsbexchange.com/?icao=C06362&showTrace=2024-09-29&timestamp=1727634949
KEWRCYOW183529SEP24
```

* 4 character origin airport code
* 4 character destination airport code
* 4 characters for current time in UTC, HH:MM
* A few options after this:
  * A UTC HH:MM time shortly before the takeoff time. Possibly the time some subsystem was turned on or when the plane started pushback.
  * A date: DDMMMYY. 29SEP24 in the last example message means September 29th, 2024.
  * A longer status message including the destination airport, the second timecode as above, possibly fuel information?

## Acronyms / Codes

...

## Analysis

Sent shortly after takeoff.
