# Opgaver – Logiske operatorer, betingelser og beslutninger

I disse opgaver skal du arbejde med `boolean`, sammenligningsoperatorer, `if`, `else if`, `else` og
de logiske operatorer `&&`, `||` og `!`.

## Kom i gang

Opret et nyt Java-projekt i IntelliJ, eller brug det projekt, du allerede har til undervisningen.

Opret en klasse med navnet:

```java
Main
```

Lav en `main`-metode i klassen:

```java
public class Main {

    public static void main(String[] args) {

    }
}
```

Lav løsningerne på opgaverne i `main`-metoden, og afprøv dem undervejs.

> **Vi bruger ikke `Scanner` i dag.** Sæt i stedet værdierne direkte i koden, og **ændr dem
> manuelt** for at afprøve de forskellige tilfælde. Det er en vigtig vane: for hver opgave skal du
> teste både det tilfælde, hvor betingelsen er sand, og det tilfælde, hvor den er falsk.

---

## Opgave 1 – Din første if

Opret en variabel:

```java
int age = 20;
```

Skriv en `if`-sætning, der udskriver:

```text
You are an adult
```

hvis alderen er 18 eller derover.

Afprøv programmet med `age = 20` og derefter med `age = 15`.

---

## Opgave 2 – Tilføj else

Udvid opgave 1, så programmet skriver:

```text
You are a minor
```

hvis alderen er under 18.

Afprøv igen med begge værdier. Tjek at der **altid** bliver skrevet præcis én linje.

---

## Opgave 3 – Positivt, negativt eller nul

Lav et program med en variabel:

```java
int number = 7;
```

Programmet skal skrive:

* `The number is positive` hvis tallet er større end 0
* `The number is negative` hvis tallet er mindre end 0
* `The number is zero` hvis tallet er 0

Afprøv med alle tre slags tal.

---

## Opgave 4 – Lige eller ulige

Lav et program, der undersøger, om et tal er lige eller ulige.

```java
int number = 8;
```

Output skal være enten:

```text
8 is even
```

eller:

```text
7 is odd
```

Hjælp: brug modulo-operatoren `%`. Et lige tal giver resten `0`, når det divideres med 2.

---

## Opgave 5 – Største af to tal

Lav et program med to variable:

```java
int a = 12;
int b = 30;
```

Programmet skal skrive det største af de to tal:

```text
The largest number is 30
```

Overvej: Hvad skal der ske, hvis de to tal er lige store? Håndtér også det tilfælde.

---

## Opgave 6 – Største af tre tal

Udvid opgave 5 til tre tal:

```java
int a = 12;
int b = 30;
int c = 25;
```

Programmet skal skrive det største af de tre.

Prøv at løse det på to måder:

1. med indlejrede `if`-sætninger
2. med `&&`

Hvilken af de to synes du er lettest at læse?

---

## Opgave 7 – Karakterskala

Lav et program med en variabel:

```java
int score = 78;
```

Programmet skal udskrive en karakter efter denne skala:

| Point | Karakter |
| --- | --- |
| 90-100 | A |
| 80-89 | B |
| 70-79 | C |
| 60-69 | D |
| under 60 | F |

Eksempel på output:

```text
Grade: C
```

Test med mindst én værdi fra hvert interval.

### Ekstra

Prøv at bytte om på rækkefølgen af dine `else if`-betingelser, så den mindste kommer først. Kør
programmet igen med `score = 95`.

Hvad sker der? Hvorfor?

---

## Opgave 8 – Må du køre bil?

Lav et program med to variable:

```java
int age = 20;
boolean hasLicense = true;
```

Programmet skal skrive `You may drive`, hvis personen er 18 eller derover **og** har kørekort.
Ellers skal det skrive `You may not drive`.

Afprøv **alle fire** kombinationer:

| age | hasLicense | Forventet |
| --- | --- | --- |
| 20 | `true` | You may drive |
| 20 | `false` | You may not drive |
| 15 | `true` | You may not drive |
| 15 | `false` | You may not drive |

---

## Opgave 9 – Tre forskellige beskeder

Udvid opgave 8, så programmet giver en mere præcis besked:

* `You may drive` – hvis begge betingelser er opfyldt
* `You need a license first` – hvis personen er gammel nok, men ikke har kørekort
* `You are too young` – hvis personen ikke er gammel nok

Overvej: kan du løse denne opgave med ét enkelt `&&`? Hvorfor / hvorfor ikke?

---

## Opgave 10 – Ekstremt vejr

Lav et program med:

```java
int temperature = 35;
```

Programmet skal skrive:

```text
Extreme weather
```

hvis temperaturen er **under 0 eller over 30**. Ellers skal det skrive:

```text
Normal weather
```

Afprøv med `-5`, `15` og `35`.

---

## Opgave 11 – Er tallet i intervallet?

Lav et program, der undersøger, om et tal ligger mellem 1 og 10 (begge inklusive).

```java
int number = 7;
```

Output:

```text
7 is between 1 and 10
```

eller:

```text
15 is not between 1 and 10
```

Afprøv med `0`, `1`, `7`, `10` og `15` – vær særlig opmærksom på de to yderpunkter.

---

## Opgave 12 – Skudår

Et årstal er et skudår, hvis:

* det er deleligt med 4, **og**
* det **ikke** er deleligt med 100, **medmindre** det også er deleligt med 400

Lav et program med:

```java
int year = 2024;
```

der skriver enten:

```text
2024 is a leap year
```

eller:

```text
2023 is not a leap year
```

Afprøv med disse årstal og tjek dine svar:

| År | Skudår? |
| --- | --- |
| 2024 | ja |
| 2023 | nej |
| 1900 | nej |
| 2000 | ja |

> Denne opgave er sværere, end den ser ud. Prøv først at skrive reglen op i ord, og oversæt den så
> til `&&` og `||`.

---

## Opgave 13 – Adgangskontrol

Lav et program med:

```java
int age = 17;
boolean hasTicket = true;
boolean isVip = false;
```

Reglerne for at komme ind til koncerten er:

* VIP'er kommer altid ind
* alle andre skal have en billet **og** være mindst 18 år

Programmet skal skrive `Welcome` eller `Access denied`.

Afprøv mindst disse fire tilfælde:

| age | hasTicket | isVip | Forventet |
| --- | --- | --- | --- |
| 17 | `true` | `false` | Access denied |
| 17 | `true` | `true` | Welcome |
| 20 | `true` | `false` | Welcome |
| 20 | `false` | `false` | Access denied |

---

## Opgave 14 – Find fejlen

Se på følgende kode:

```java
int age = 15;

if (age >= 18);
{
    System.out.println("You are an adult");
}
```

Besvar:

1. Hvad udskriver programmet?
2. Hvorfor?
3. Ret fejlen.

---

## Opgave 15 – Find fejlen igen

Se på følgende kode:

```java
int number = 5;

if (1 <= number <= 10) {
    System.out.println("The number is between 1 and 10");
}
```

Besvar:

1. Vil programmet overhovedet køre?
2. Hvad siger compileren?
3. Ret koden, så den gør det, der var meningen.

---

## Opgave 16 – Ryd op i koden

Skriv følgende kode om, så den bliver kortere og lettere at læse. Den skal gøre præcis det samme.

```java
boolean isStudent = true;

if (isStudent == true) {
    System.out.println("Discount");
}
else {
    if (isStudent == false) {
        System.out.println("Full price");
    }
}
```

---

## Opgave 17 – Forudsig resultatet

Skriv **først** ned, hvad du tror hvert program udskriver. Kør dem derefter, og sammenlign.

### a

```java
int x = 10;

if (x > 5) {
    System.out.println("A");
}
else if (x > 8) {
    System.out.println("B");
}
```

### b

```java
int x = 10;

if (x > 5) {
    System.out.println("A");
}

if (x > 8) {
    System.out.println("B");
}
```

### c

```java
boolean a = true;
boolean b = false;

System.out.println(a && b);
System.out.println(a || b);
System.out.println(!a || b);
System.out.println(a && !b);
```

### d

```java
int number = 0;

if (number > 0) {
    System.out.println("positive");
}
else if (number < 0) {
    System.out.println("negative");
}
```

> Hvad blev der skrevet ud i **d**? Er det, hvad du forventede? Hvad mangler der?

---

## Opgave 18 – Billetpris

Lav et program, der beregner prisen på en biografbillet.

```java
int age = 25;
boolean isStudent = false;
```

Reglerne er:

* børn under 12 år: 50 kr.
* studerende: 80 kr.
* pensionister (65 år og derover): 70 kr.
* alle andre: 110 kr.

Programmet skal skrive:

```text
Price: 110 kr
```

Overvej rækkefølgen af dine betingelser. Hvad hvis en person både er studerende og under 12 år?
Beslut dig for, hvad der skal gælde, og skriv det som en kommentar i koden.

---

## Opgave 19 – Sandhedstabel i kode

Lav et program, der udskriver hele sandhedstabellen for `&&`:

```text
true  && true  = true
true  && false = false
false && true  = false
false && false = false
```

Du skal ikke bruge løkker – skriv de fire linjer, og lad Java beregne resultaterne med
`System.out.println`.

### Ekstra

Lav det samme for `||`.

---

## Udfordring 1 – Rock, paper, scissors

Lav et program med to variable:

```java
String player1 = "rock";
String player2 = "scissors";
```

Programmet skal skrive, hvem der vinder:

```text
Player 1 wins
```

Reglerne er: rock slår scissors, scissors slår paper, paper slår rock. Er de ens, er det uafgjort.

Til at sammenligne tekst skal du bruge `.equals()` og ikke `==`:

```java
if (player1.equals("rock")) {
    ...
}
```

> Vi skal se nærmere på, hvorfor tekst sammenlignes med `.equals()`, når vi arbejder med Strings.
> For nu: brug `.equals()` til tekst og `==` til tal og boolean.

---

## Udfordring 2 – Trekantens type

Lav et program med tre sidelængder:

```java
int a = 3;
int b = 4;
int c = 5;
```

Programmet skal først undersøge, om de tre længder overhovedet **kan** danne en trekant. Det kan de,
hvis summen af to vilkårlige sider altid er større end den tredje.

Hvis de kan, skal programmet skrive, om trekanten er:

* `Equilateral` – alle tre sider er lige lange
* `Isosceles` – præcis to sider er lige lange
* `Scalene` – ingen sider er lige lange

Hvis de ikke kan, skal det skrive `Not a triangle`.

Afprøv med:

| a | b | c | Forventet |
| --- | --- | --- | --- |
| 3 | 4 | 5 | Scalene |
| 5 | 5 | 5 | Equilateral |
| 5 | 5 | 8 | Isosceles |
| 1 | 2 | 10 | Not a triangle |

---

## Udfordring 3 – Den ternære operator

Skriv disse to programmer om, så de bruger den ternære operator `? :` i stedet for `if`/`else`:

### a

```java
int age = 20;
String status;

if (age >= 18) {
    status = "adult";
}
else {
    status = "minor";
}

System.out.println(status);
```

### b

```java
int a = 12;
int b = 30;
int largest;

if (a > b) {
    largest = a;
}
else {
    largest = b;
}

System.out.println(largest);
```

Diskutér i gruppen: I hvilke af de to tilfælde bliver koden faktisk **lettere** at læse?
