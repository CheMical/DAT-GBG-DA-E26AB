# Opgaver – While-loops

I disse opgaver skal du arbejde med `while`-loops og `do-while` i Java.

## Kom i gang

Opret et nyt Java-projekt i IntelliJ.

Opret herefter en klasse med navnet:

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

Lav løsningerne på opgaverne i `main`-metoden og afprøv dem undervejs.

---

## Opgave 1 – Tæl fra 1 til 10

Lav et `while`-loop, der skriver tallene fra 1 til 10.

Forventet output:

```text
1
2
3
4
5
6
7
8
9
10
```

---

## Opgave 2 – Tæl ned

Lav et `while`-loop, der tæller ned fra 10 til 1.

Når loopet er færdigt, skal programmet skrive:

```text
Start!
```

---

## Opgave 3 – Lige tal

Lav et `while`-loop, der skriver de lige tal fra 2 til 20.

Forventet output:

```text
2
4
6
8
10
12
14
16
18
20
```

---

## Opgave 4 – Gangetabel

Lav et program, der ved hjælp af et `while`-loop skriver 5-tabellen:

```text
5
10
15
20
25
30
35
40
45
50
```

### Ekstra

Kan du ændre programmet, så det skriver:

```text
1 * 5 = 5
2 * 5 = 10
3 * 5 = 15
...
10 * 5 = 50
```

---

## Opgave 5 – Summen af tal

Lav et `while`-loop, der beregner summen af tallene fra 1 til 10.

Resultatet skal være:

```text
Summen er 55
```

Du får sandsynligvis brug for to variable:

```java
int number = 1;
int sum = 0;
```

Overvej:

* Hvilken variabel styrer loopet?
* Hvilken variabel indeholder den samlede sum?

---

## Opgave 6 – Gæt et tal

Lav et program, hvor brugeren skal gætte et bestemt tal.

Start fx med:

```java
int secretNumber = 7;
```

Brug `Scanner` til at læse brugerens gæt.

Programmet skal blive ved med at spørge:

```text
Gæt tallet:
```

så længe brugeren ikke har gættet `7`.

Når tallet bliver gættet, skal programmet skrive:

```text
Du gættede rigtigt!
```

---

## Opgave 7 – Gæt højere eller lavere

Udvid opgave 6.

Hvis brugerens gæt er mindre end det hemmelige tal, skal programmet skrive:

```text
For lavt
```

Hvis brugerens gæt er større end det hemmelige tal, skal programmet skrive:

```text
For højt
```

Eksempel:

```text
Gæt tallet: 3
For lavt

Gæt tallet: 9
For højt

Gæt tallet: 7
Du gættede rigtigt!
```

---

## Opgave 8 – Hvor mange forsøg?

Udvid gættespillet, så programmet tæller, hvor mange forsøg brugeren har brugt.

Eksempel:

```text
Gæt tallet: 4
For lavt

Gæt tallet: 8
For højt

Gæt tallet: 7
Du gættede rigtigt!

Antal forsøg: 3
```

---

## Opgave 9 – Stop med 0

Lav et program, der bliver ved med at bede brugeren om at indtaste et tal.

Programmet skal stoppe, når brugeren indtaster:

```text
0
```

Eksempel:

```text
Indtast et tal: 4
Indtast et tal: 12
Indtast et tal: 3
Indtast et tal: 0

Programmet stopper.
```

---

## Opgave 10 – Beregn summen af brugerens tal

Udvid opgave 9.

Programmet skal lægge alle de indtastede tal sammen.

Tallet `0` skal ikke medregnes.

Eksempel:

```text
Indtast et tal: 5
Indtast et tal: 3
Indtast et tal: 10
Indtast et tal: 0

Summen er: 18
```

---

## Opgave 11 – do-while

Lav denne opgave med et `do-while`-loop.

Programmet skal bede brugeren om at skrive et positivt tal.

```text
Indtast et positivt tal:
```

Hvis brugeren skriver `0` eller et negativt tal, skal programmet spørge igen.

Eksempel:

```text
Indtast et positivt tal: -3
Indtast et positivt tal: 0
Indtast et positivt tal: 8

Tak!
```

Overvej:

> Hvorfor passer `do-while` godt til denne opgave?

---

## Opgave 12 – Find fejlen

Se på følgende kode:

```java
int number = 1;

while (number <= 10) {
    System.out.println(number);
}
```

Besvar følgende:

1. Hvad sker der, når programmet køres?
2. Hvorfor sker det?
3. Ret koden, så programmet skriver tallene fra 1 til 10.

---

## Opgave 13 – Forudsig resultatet

Se på koden uden at køre den først:

```java
int number = 10;

while (number > 4) {
    System.out.println(number);
    number = number - 2;
}
```

Skriv ned, hvad du tror programmet udskriver.

Kør derefter programmet og kontroller dit svar.

---

## Opgave 14 – Tegn loopet

Tegn et aktivitetsdiagram for følgende kode:

```java
int number = 1;

while (number <= 5) {
    System.out.println(number);
    number++;
}

System.out.println("Loopet er slut");
```

Diagrammet skal som minimum vise:

* initialisering af `number`
* betingelsen `number <= 5`
* udskriften
* `number++`
* hvad der sker, når betingelsen bliver falsk

Du må gerne bruge Mermaid.

---

## Udfordring – Lille menu

Lav et program, der viser denne menu:

```text
1. Sig hej
2. Vis et tal
3. Afslut
```

Brugeren vælger ved at indtaste `1`, `2` eller `3`.

Programmet skal vise menuen igen efter hvert valg.

Hvis brugeren vælger `3`, stopper programmet.

Eksempel:

```text
1. Sig hej
2. Vis et tal
3. Afslut

Vælg: 1
Hej!

1. Sig hej
2. Vis et tal
3. Afslut

Vælg: 2
Tallet er 42

1. Sig hej
2. Vis et tal
3. Afslut

Vælg: 3
Farvel!
```

Her skal du kombinere:

* `while`
* `Scanner`
* `if` / `else if`
* variable
