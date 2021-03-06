# pwcheck

## School project (Introduction to Programming Systems, C)
Evaluation: TBA

# EN

The goal of the project is to create a program that receives a set of passwords at the input and checks each of them against all (fixed) necessary rules. Passwords that have been verified will be displayed, the rest will be discarded. Input data (password list) will be read from standard input (stdin), output data (filtered password list) will be printed to standard output (stdout).

## Compile

`gcc -std=c99 -Wall -Wextra -Werror pwcheck.c -o pwcheck`

## Execution syntax

`./pwcheck [--help] LEVEL PARAM [--stats]`

| Command | Description |
| --- | --- |
| `LEVEL` | An integer in the interval [1, 4] that specifies the required security level (see below) |
| `PARAM` | A positive integer that specifies an additional rule parameter (see below) |
| `--stats` | If specified, determines whether summary statistics of the analyzed passwords should be displayed at the end of the program. |
| `--help` | Shows the correct ways to work with the program. |

## Security levels (controlled rules)

A total of 4 security levels are defined, expressed using 4 rules. The security level specifies that passwords must comply with all rules at that and lower levels. Ie. for example, security level 3 specifies that passwords must comply with rules 1, 2, and 3.

Some rules are parameterizable by an integer specified using the PARAM program argument. In the following list, this parameter is marked as X.

## List of rules

1. The password contains at least 1 uppercase and 1 lowercase letter.
2. The password contains characters from at least X groups. The groups considered are:
    - lowercase letters (a-z)
    - uppercase letters (A-Z)
    - numbers (0-9)
    - special characters (at least non-alphanumeric characters from the ASCII table in positions 33-126 must be supported)
3. The password does not contain the same sequence of characters of at least X.
4. The password does not contain two identical substrings of at least X.

## Statistics

If the specified argument is the --stats program, the program must print total statistics at the end of the output in the format:

```
Statistics:
Different characters: NCHARS
Minimum length: MIN
Average length: AVG
```

| Argument | Description |
| --- | --- |
| `NCHARS` | The number of different characters that appear across all passwords. |
| `MIN` | Length of the shortest password (or passwords). |
| `AVG` | Average length of the password (arithmetic mean) rounded to 1 decimal place. |

## Implementation details

### Input data (password list)

The list of passwords is passed to the program on standard input (stdin). Each password is entered on a separate line and contains only ASCII text data, except for the newline character. The maximum length of the password is 100 characters, otherwise it is invalid data. The program must support an unlimited number of passwords on entry.

### Program output

The standard output program (stdout) prints passwords from the input list, each on a separate line, that meet the required security level specified as the LEVEL program argument. Passwords must be listed without change and in the same order as they appeared on the entry.

After the output list of passwords, the program optionally lists statistics.


# CZ

C??lem projektu je vytvo??it program, kter?? na vstupu dostane sadu hesel a pro ka??d?? z nich ov??????, jestli heslo spl??uje v??echna (pevn?? zadan??) po??adovan?? pravidla. Ta hesla, kter?? projdou kontrolou, budou vypisov??na na v??stup, ostatn?? budou zahozena. Vstupn?? data (seznam hesel) budou ??tena ze standardn??ho vstupu (stdin), v??stup (filtrovan?? seznam hesel) bude tisknut na standardn?? v??stup (stdout).

## P??eklad zdrojov??ho souboru:

`gcc -std=c99 -Wall -Wextra -Werror pwcheck.c -o pwcheck`

## Syntax spu??t??n??

`./pwcheck LEVEL PARAM [--stats]`

| P????kaz | Popis |
| --- | --- |
| `LEVEL` | Cel?? ????slo v intervalu [1, 4], kter?? ur??uje po??adovanou ??rove?? bezpe??nosti (viz n????e). |
| `PARAM` | Kladn?? cel?? ????slo, kter?? ur??uje dodate??n?? parametr pravidel (viz n????e). |
| `--stats` | Pokud je zadan??, ur??uje, zda se na konci programu maj?? vypsat souhrnn?? statistiky analyzovan??ch hesel. |
| `--help` | Ukazuje spr??vn?? zp??sob pr??ce s programem. |

## ??rovn?? bezpe??nosti (kontrolovan?? pravidla)

Jsou definov??ny celkem 4 ??rovn?? bezpe??nosti vyj??d??eny pomoc?? 4 pravidel. ??rove?? bezpe??nosti ur??uje, ??e hesla mus?? spl??ovat v??echna pravidla na dan?? a ni?????? ??rovni. Tzn. nap??. ??rove?? bezpe??nosti 3 specifikuje, ??e hesla mus?? spl??ovat pravidla 1, 2 a 3.

N??kter?? pravidla jsou parametrizovateln?? cel??m ????slem zadan??m pomoc?? argumentu programu PARAM. V n??sleduj??c??m seznamu je tento parametr ozna??en jako X.

## Seznam pravidel:

1. Heslo obsahuje alespo?? 1 velk?? a 1 mal?? p??smeno.
2. Heslo obsahuje znaky z alespo?? X skupin. Uva??ovan?? skupiny jsou:
    - mal?? p??smena (a-z)
    - velk?? p??smena (A-Z)
    - ????sla (0-9)
    - speci??ln?? znaky (podporovan?? mus?? b??t alespo?? nealfanumerick?? znaky z ASCII tabulky na pozic??ch 33-126)
3. Heslo neobsahuje sekvenci stejn??ch znak?? d??lky alespo?? X.
4. Heslo neobsahuje dva stejn?? pod??et??zce d??lky alespo?? X.

## Statistiky

Pokud je zadan?? argument programu --stats, program mus?? na konec v??stupu vypsat celkov?? statistiky ve form??tu:
```
Statistics:
Different characters: NCHARS
Minimum length: MIN
Average length: AVG
```
| Prom??nn?? | Popis |
| --- | --- |
| `NCHARS` | Po??et r??zn??ch znak?? vyskytuj??c??ch se nap?????? v??emi hesly. |
| `MIN` | d??lka nejkrat????ho hesla (resp. hesel). |
| `AVG` | pr??m??rn?? d??lka hesla (aritmetick?? pr??m??r) zaokrouhlen?? na 1 desetin?? m??sto. |

## Implementa??n?? detaily

### Vstupn?? data (seznam hesel)

Seznam hesel je programu p??ed??n na standardn??m vstupu (stdin). Ka??d?? heslo je zad??no na samostatn??m ????dku a obsahuje pouze ASCII textov?? data, krom?? znaku nov??ho ????dku. Maxim??ln?? d??lka hesla je 100 znak??, jinak se jedn?? o nevalidn?? data. Program mus?? podporovat neomezen?? po??et hesel na vstupu.

### V??stup programu

Program na standardn?? v??stup (stdout) vypisuje hesla ze vstupn??ho seznamu, ka??d?? na samostatn?? ????dek, kter?? spl??uj?? po??adovanou ??rove?? bezpe??nosti zadanou jako argument programu LEVEL. Hesla mus?? b??t vyps??na beze zm??ny a ve stejn??m po??ad?? jako se objevila na vstupu.

Za v??stupn??m seznamem hesel pak program voliteln?? vypisuje statistiku.