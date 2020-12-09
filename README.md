# dln-encoder


## Objective

For a long time, the state of Washington used an algorithm (explained below) to generate driver's license numbers derived from a driver's name and date of birth.

You will be creating a "drivers license calculator" to generate the DLN given someone's name and birth date.

Use your knowledge of javascript to fill in the stubbed methods in `src/index.html`.

## The Algorithm

Thankfully, since Marist college published the algorithm many moons ago, we do not have to derive this algorithm ourselves!

Here is what they found:
( From http://web.archive.org/web/20061206063841/http://www.academic.marist.edu/mwa/wsdln.htm )

1) The first five characters are the first five letters of the individuals surname (last name). If an individuals last name contains 4 or fewer letters, the symbol * is used to fill in the remaining spaces.
2) The sixth character is the individuals first initial.
3) The seventh character is the individuals middle initial. The symbol * is used if an individual does not have a middle name.
4) The next two characters are obtained by computing subtracting the individuals year-of-birth (YOB) from 100. In other words, 100 - YOB.
5) The tenth character is the check digit.
6) The eleventh character is the month-of-birth code. It assigns a character according to the code presented in the table below. The alternate codes are used to avoid collisions.

| Month     | Code | Alternate Code
| --------- | ----- |---------------|
|January	|  B	|  S            |
|February	|  C	|  T            |
|March	    |  D	|  U            |
|April	    |  J	|  1            |
|May	    |  K	|  2            |
|June	    |  L	|  3            |
|July	    |  M	|  4            |
|August 	|  N	|  5            |
|Septebmer	|  O	|  6            |
|October	|  P	|  7            |
|November	|  Q	|  8            |
|December	|  R	|  9            |


7) The last character is the code for the day of the month on which the individaul was born. The day-of-month-born code is presented in the table below.

| Day | Code |
| --- | ---- |
|  1  |   A  |
|  2  |   B  |
|  3  |   C  |
|  4  |   D  |
|  5  |   E  |
|  6  |   F  |
|  7  |   G  |
|  8  |   H  |
|  9  |   Z  |
|  10 |   S  |
|  11 |   J  |
|  12 |   K  |
|  13 |   L  |
|  14 |   M  |
|  15 |   N  |
|  16 |   W  |
|  17 |   P  |
|  18 |   Q  |
|  19 |   R  |
|  20 |   O  |
|  21 |   1  |
|  22 |   2  |
|  23 |   3  |
|  24 |   4  |
|  25 |   5  |
|  26 |   2  |
|  27 |   7  |
|  28 |   8  |
|  29 |   9  |
|  30 |   T  |
|  31 |   U  |

| Character | Code |
| --------- | ---- |
| *         |   0  |
| A         |   1  |
| B         |   2  |
| C         |   3  |
| D         |   4  |
| E         |   5  |
| F         |   6  |
| G         |   7  |
| H         |   8  |
| I         |   9  |
| J         |   1  |
| K         |   2  |
| L         |   3  |
| M         |   4  |
| N         |   5  |
| O         |   6  |
| P         |   7  |
| Q         |   8  |
| R         |   9  |
| S         |   2  |
| T         |   3  |
| U         |   4  |
| V         |   5  |
| W         |   6  |
| X         |   7  |
| Y         |   8  |
| Z         |   9  |

Examples:
Driver Information	License Number
Joseph Marshall Pollan 	POLLAJM304PR
Born: October 19, 1970	
Tracy Holland 	HOLLAT*554J5
Born: April 25, 1945	
Alexander William Moe	MOE**AW240MD
Born: July 4, 1976	
 

The Check Digit Scheme:

    Consider the twelve character Washington State/Manitoba Province
driver's license number a1a2a3a4a5a6a7a8a9a10a11a12. 
The check digit a10 is created by first assigning digits to the non-digit characters in the identification number using the table below and then performing the following calculation:

a10 = |a1-a2+a3-a4+a5-a6+a7-a8+a9-a11+a12| (mod 10)


