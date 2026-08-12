# Opgaver – Variable, datatyper og aritmetiske operatorer

I disse opgaver skal du arbejde med:

* variable
* datatyper
* aritmetiske operatorer
* operatorprioritet
* heltalsdivision
* `++` og `--`

Forsøg så vidt muligt selv at løse opgaverne, før du sammenligner med andre.

---

# Sådan arbejder du med opgaverne

Du må gerne løse alle opgaver i den samme `main`-metode.

Det kan være en god idé at skrive en overskrift før hver opgave:

```java
System.out.println("Opgave 1");

int age = 25;

System.out.println(age);
```

Du kan også udkommentere kode, du ikke arbejder med lige nu:

```java
// int age = 25;
// System.out.println(age);
```

# Del 1 – Variable

## Opgave 1 – Din første variabel

Opret en variabel:

```java
int age = 20;
```

Skriv værdien ud med:

```java
System.out.println(age);
```

Prøv derefter at ændre værdien.

---

## Opgave 2 – Flere variable

Opret variable til:

* dit navn
* din alder
* din højde
* om du er studerende

Vælg selv passende datatyper.

Skriv alle værdierne ud.

Eksempel på output:

```text
Navn: Anna
Alder: 22
Højde: 1.72
Studerende: true
```

---

## Opgave 3 – Skift værdi

Opret:

```java
int score = 10;
```

Skriv værdien ud.

Ændr derefter værdien til `20` og skriv den ud igen.

Programmet skal altså vise:

```text
10
20
```

---

# Del 2 – Datatyper

## Opgave 4 – Vælg datatype

Vælg en passende datatype til hver af følgende oplysninger:

* antal studerende på et hold
* en persons højde
* en persons navn
* om en bruger er logget ind
* et bogstav
* antallet af visninger på en meget populær video

Opret en variabel til hver.

---

## Opgave 5 – `int` og `double`

Opret:

```java
int numberOfStudents = 27;
double averageHeight = 1.78;
```

Skriv begge værdier ud.

Prøv derefter at ændre:

```java
double averageHeight
```

til:

```java
int averageHeight
```

Hvad sker der?

Hvorfor?

---

## Opgave 6 – `long`

En video har fået:

```text
4.500.000.000
```

visninger.

Opret en variabel, der kan indeholde dette tal.

Skriv værdien ud.

---

## Opgave 7 – `float` og `double`

Opret først:

```java
double temperature = 21.5;
```

Lav derefter den samme variabel som en `float`.

Hvad skal du ændre?

---

# Del 3 – Simple beregninger

## Opgave 8 – Addition

Opret:

```java
int a = 10;
int b = 5;
```

Beregn summen af de to tal og gem resultatet i en ny variabel:

```java
int result = ...
```

Skriv resultatet ud.

---

## Opgave 9 – De fire regnearter

Brug:

```java
int a = 20;
int b = 4;
```

Beregn og skriv:

* `a + b`
* `a - b`
* `a * b`
* `a / b`

---

## Opgave 10 – Prisberegning

En sodavand koster `18.5` kr.

En kunde køber `4` sodavand.

Opret variable til:

* pris
* antal
* samlet pris

Beregn den samlede pris og skriv den ud.

Forventet resultat:

```text
74.0
```

---

## Opgave 11 – Rektangel

Et rektangel har:

```text
bredde = 8
højde = 5
```

Beregn rektanglets areal.

Formlen er:

```text
areal = bredde * højde
```

Skriv resultatet ud.

---

# Del 4 – Division og modulo

## Opgave 12 – Heltalsdivision

Hvad tror du, dette program skriver ud?

```java
int result = 7 / 2;

System.out.println(result);
```

Skriv dit bud ned **før** du kører programmet.

Kør derefter programmet.

Forklar resultatet.

---

## Opgave 13 – Få decimalerne med

Ændr programmet fra forrige opgave, så resultatet bliver:

```text
3.5
```

---

## Opgave 14 – Rest ved division

Hvad bliver resultatet af:

```java
17 % 5
```

Skriv først dit bud ned.

Afprøv derefter:

```java
int result = 17 % 5;

System.out.println(result);
```

---

## Opgave 15 – Lige eller ulige

Prøv følgende værdier:

```java
int number = 8;
```

og:

```java
int number = 9;
```

Skriv:

```java
System.out.println(number % 2);
```

Hvilket resultat får du for lige tal?

Hvilket resultat får du for ulige tal?

---

# Del 5 – Operatorprioritet

## Opgave 16 – Forudsig resultatet

Hvad bliver resultatet?

```java
int result = 2 + 3 * 4;
```

Skriv dit svar ned, før du kører programmet.

---

## Opgave 17 – Parenteser

Hvad bliver resultatet?

```java
int result = (2 + 3) * 4;
```

Hvorfor er resultatet forskelligt fra forrige opgave?

---

## Opgave 18 – Flere operatorer

Forudsig resultatet af:

```java
int result = 10 + 12 / 3 * 2;
```

Kør derefter programmet.

Prøv at forklare, i hvilken rækkefølge Java udfører beregningen.

---

## Opgave 19 – Brug parenteser

Du har:

```java
int a = 10;
int b = 5;
int c = 2;
```

Skriv et udtryk, der først lægger `a` og `b` sammen og derefter ganger resultatet med `c`.

Resultatet skal være:

```text
30
```

---

# Del 6 – Ændring af variable

## Opgave 20 – Læg til en variabel

Opret:

```java
int score = 10;
```

Læg `5` til værdien ved at skrive:

```java
score = score + 5;
```

Skriv resultatet ud.

---

## Opgave 21 – `+=`

Løs forrige opgave igen, men denne gang skal du bruge:

```java
+=
```

---

## Opgave 22 – Flere sammensatte operatorer

Start med:

```java
int number = 10;
```

Udfør derefter følgende:

1. læg `5` til
2. gang med `2`
3. træk `10` fra

Brug:

```text
+=
*=
-=
```

Hvad bliver den endelige værdi?

---

# Del 7 – `++` og `--`

## Opgave 23 – Increment

Opret:

```java
int count = 5;
```

Brug:

```java
count++;
```

Skriv værdien ud.

Hvad bliver resultatet?

---

## Opgave 24 – Flere increments

Start med:

```java
int count = 10;
```

Brug `count++` tre gange.

Skriv derefter værdien ud.

---

## Opgave 25 – Decrement

Start med:

```java
int lives = 3;
```

Brug:

```java
lives--;
```

to gange.

Skriv værdien ud.

---

## Opgave 26 – Tre måder at lægge 1 til

Start med:

```java
int number = 10;
```

Afprøv hver af følgende måder:

```java
number = number + 1;
```

```java
number += 1;
```

```java
number++;
```

Hvad har de tre udtryk til fælles?

---

# Del 8 – `x++` og `++x`

## Opgave 27 – Post-increment

Forudsig først resultatet:

```java
int x = 5;

int y = x++;

System.out.println(x);
System.out.println(y);
```

Kør derefter programmet.

Forklar med dine egne ord, hvad der sker.

---

## Opgave 28 – Pre-increment

Forudsig resultatet:

```java
int x = 5;

int y = ++x;

System.out.println(x);
System.out.println(y);
```

Kør programmet.

Hvad er forskellen på denne opgave og den forrige?

---

## Opgave 29 – `--`

Hvad bliver værdierne af `x` og `y`?

```java
int x = 10;

int y = x--;

System.out.println(x);
System.out.println(y);
```

Prøv derefter:

```java
int x = 10;

int y = --x;

System.out.println(x);
System.out.println(y);
```

Forklar forskellen.

---

# Del 9 – Sammensatte opgaver

## Opgave 30 – Indkøb

En kunde køber:

* 3 sandwiches til 42 kr. stykket
* 2 sodavand til 18 kr. stykket

Opret passende variable.

Beregn den samlede pris.

Forventet resultat:

```text
162
```

---

## Opgave 31 – Gennemsnitsalder

Tre personer er:

```text
20 år
24 år
28 år
```

Beregn deres gennemsnitsalder.

Pas på med heltalsdivision.

Resultatet skal være:

```text
24.0
```

---

## Opgave 32 – Sekunder

Du har:

```java
int seconds = 367;
```

Beregn:

* hvor mange hele minutter det svarer til
* hvor mange sekunder der er tilbage

Brug både `/` og `%`.

Forventet resultat:

```text
6 minutter
7 sekunder
```

---

## Opgave 33 – Timer, minutter og sekunder

Du har:

```java
int seconds = 7384;
```

Beregn hvor mange:

* timer
* minutter
* sekunder

det svarer til.

Forventet resultat:

```text
2 timer
3 minutter
4 sekunder
```

**Hint:** Du får brug for både `/` og `%`.

---

## Opgave 34 – Temperatur

En temperatur er målt til:

```java
double celsius = 20.0;
```

Temperaturen i Fahrenheit kan beregnes sådan:

```text
fahrenheit = celsius * 9 / 5 + 32
```

Beregn temperaturen i Fahrenheit.

Forventet resultat:

```text
68.0
```

---

## Opgave 35 – Rabat

En vare koster:

```text
800 kr.
```

Der gives:

```text
25 %
```

rabat.

Opret variable til:

* pris
* rabatprocent
* rabat i kroner
* pris efter rabat

Beregn den nye pris.

Forventet resultat:

```text
600.0
```

---

# Udfordringer

Disse opgaver er lidt sværere. Prøv dem, hvis du er kommet godt igennem de øvrige opgaver.

## Opgave 36 – Byt værdier

Du har:

```java
int a = 5;
int b = 10;
```

Din opgave er at bytte værdierne, så:

```text
a = 10
b = 5
```

Du må ikke skrive:

```java
a = 10;
b = 5;
```

Du skal bruge de eksisterende variable og må gerne oprette én ekstra variabel.

---

## Opgave 37 – Dage til timer

Opret:

```java
int days = 7;
```

Beregn hvor mange:

* timer
* minutter
* sekunder

der er i det antal dage.

---

## Opgave 38 – Forudsig programmet

Læs programmet uden at køre det:

```java
int x = 5;
int y = 2;

x += 3;
y++;

int result = x * y + 4;

System.out.println(x);
System.out.println(y);
System.out.println(result);
```

Skriv ned, hvad du forventer bliver skrevet ud.

Kør derefter programmet og kontroller dit svar.

---

## Opgave 39 – Find fejlen

Følgende program indeholder fejl:

```java
int age = "25";
double price = 19,95;
float temperature = 21.5;
long population = 5000000000;

System.out.println(age);
```

Find og ret fejlene.

---

## Opgave 40 – Lav dit eget udtryk

Opret tre variable:

```java
int a = 5;
int b = 10;
int c = 2;
```

Lav et aritmetisk udtryk, der bruger alle tre variable og mindst tre forskellige operatorer.

Prøv derefter at:

1. forudsige resultatet
2. køre programmet
3. ændre parenteserne
4. undersøge hvordan resultatet ændrer sig

