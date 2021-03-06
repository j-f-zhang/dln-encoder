# Driver's License Number Encoder

## About

Up until [as recently as 2018](https://www.king5.com/article/news/local/washington-drivers-license-numbers-change-tuesday/281-587296223), Washington state issued driver's license numbers based on the driver's name and birthdate. The algorithm was widely known and had the potential for abuse: if you knew someone's full name and date of birth, you could get their license number! Thankfully, it's now a secure randomly generated number, but let's use their algorithm as a basis for [exploring some concepts in JavaScript](https://drive.google.com/file/d/1FrzGH4SMEscvGplEMh_CRChfsR2vVReI/view?usp=sharing)!

## Getting started

This repository contains a very simple web page. It doesn't work right now, but by the end of the lesson, you will have a functioning drivers license number encoder!
 
1. To download the source code, find "Download ZIP" in the "Code" dropdown.

2. Extract your zip file into your working folder -- `C://source/dln-encoder-main`.

3. If you don't already have a preferred text editor, download Visual Studio Code for your machine [here](https://code.visualstudio.com/download).

4. Use your text editor to open the `dln-encoder-main` folder.

5. Open a web browser (you will be using this for verifying your work throughout the lesson).

6. Type the location of your index file `C://source/dln-encoder-main/src/index.html` into the browser.

7. Make sure you can see a form with name and birthday input, and a "submit" button. (Don't panic! Your submit button shouldn't do anything yet. :) )

8. Use your knowledge of javascript to fill in the stubbed methods in `src/index.html`.

## The Algorithm

Thankfully, since Marist college [published the algorithm](http://web.archive.org/web/20061206063841/http://www.academic.marist.edu/mwa/wsdln.htm) long ago, we do not have to derive this algorithm ourselves!

Here is what they found:

1) The first five characters are the first five letters of the individual's surname (last name). If an individual's last name contains 4 or fewer letters, the symbol * is used to fill in the remaining spaces.
2) The sixth character is the individual's first initial.
3) The seventh character is the individual's middle initial. The symbol * is used if an individual does not have a middle name.
4) The next two characters are obtained by computing subtracting the individual's year-of-birth (YOB) from 100. In other words, 100 - YOB.
5) The tenth character is the [check digit](#The-Check-Digit-Scheme). (To be calculated after all other characters are found.)
6) The eleventh character is the month-of-birth code. It assigns a character according to the code presented in the table below. (The alternate codes are used to avoid collisions in the case two individuals end up with the same driver's license number -- but don't worry about this during our lesson today!)

|Month|Code|Alternate Code|
|---------|-----|---------------|
|January|B|S|
|February|C|T|
|March|D|U|
|April|J|1|
|May|K|2|
|June|L|3|
|July|M|4|
|August|N|5|
|Septebmer|O|6|
|October|P|7|
|November|Q|8|
|December|R|9|


7) The last character is the code for the day of the month on which the individaul was born. The day-of-month-born code is presented in the table below.

|Day|Code|
|---|----|
|1|A|
|2|B|
|3|C|
|4|D|
|5|E|
|6|F|
|7|G|
|8|H|
|9|Z|
|10|S|
|11|J|
|12|K|
|13|L|
|14|M|
|15|N|
|16|W|
|17|P|
|18|Q|
|19|R|
|20|O|
|21|1|
|22|2|
|23|3|
|24|4|
|25|5|
|26|2|
|27|7|
|28|8|
|29|9|
|30|T|
|31|U|

## The Check Digit Scheme

Consider the twelve character driver's license number a<sub>1</sub>a<sub>2</sub>a<sub>3</sub>a<sub>4</sub>a<sub>5</sub>a<sub>6</sub>a<sub>7</sub>a<sub>8</sub>a<sub>9</sub>a<sub>10</sub>a<sub>11</sub>a<sub>12</sub>.

The check digit a<sub>10</sub> is created by first assigning digits to the non-digit characters in the identification number using the table below and then performing the following calculation:

a<sub>10</sub> = |a<sub>1</sub>-a<sub>2</sub>+a<sub>3</sub>-a<sub>4</sub>+a<sub>5</sub>-a<sub>6</sub>+a<sub>7</sub>-a<sub>8</sub>+a<sub>9</sub>-a<sub>11</sub>+a<sub>12</sub>| (mod 10)

|Character|Digit|
|---------|----|
|*|0|
|A|1|
|B|2|
|C|3|
|D|4|
|E|5|
|F|6|
|G|7|
|H|8|
|I|9|
|J|1|
|K|2|
|L|3|
|M|4|
|N|5|
|O|6|
|P|7|
|Q|8|
|R|9|
|S|2|
|T|3|
|U|4|
|V|5|
|W|6|
|X|7|
|Y|8|
|Z|9|

## Examples
|Driver Information|License Number|
|---|---|
|Joseph Marshall Pollan: October 19, 1970|POLLAJM304PR|
|Tracy Holland: April 25, 1945|HOLLAT*554J5|
|Alexander William Moe: July 4, 1976|MOE**AW240MD|
	
## The Key
https://github.com/j-f-zhang/dln-encoder-key

