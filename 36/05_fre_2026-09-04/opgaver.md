# Opgaver – Loops og Strings. Repetition og opsamling

Dagens opgaver falder i tre dele:

1. **Strings** – de nye metoder
2. **Loops og Strings sammen** – de fire mønstre anvendt på tekst
3. **Opsamling** – større opgaver, hvor alt fra uge 35-36 skal bruges

Nå så langt du kan. Del 3 er der næppe tid til det hele – vælg de opgaver, der ser mest
interessante ud.

## Kom i gang

Opret en klasse `Main` med en `main`-metode. Husk importen, hvor du bruger `Scanner`:

```java
import java.util.Scanner;
```

---

## Del 1 – String-metoder

### Opgave 1 – Længde og tegn

Lav en variabel:

```java
String name = "Datamatiker";
```

Skriv ud:

* hvor mange tegn navnet har
* det første tegn
* det sidste tegn (brug `length()` – skriv ikke tallet selv)

### Opgave 2 – Substring

Med samme tekst som ovenfor, skriv ud:

* de første 4 tegn
* alt fra og med index 4
* tegnene fra index 4 til og med index 7

### Opgave 3 – indexOf

```java
String sentence = "Java is a programming language";
```

Skriv ud:

* på hvilket index `"programming"` starter
* på hvilket index det første `"a"` står
* hvad `indexOf("Python")` giver

Skriv derefter et `if`, der udskriver `Fundet` eller `Ikke fundet` afhængigt af resultatet.

### Opgave 4 – Store og små bogstaver

```java
String text = "  Hello World  ";
```

Skriv ud:

* teksten med store bogstaver
* teksten med små bogstaver
* teksten uden mellemrum i enderne
* længden **før** og **efter** `trim()`

### Opgave 5 – Den der ikke ændrer sig

Kør denne kode:

```java
String text = "hello";

text.toUpperCase();

System.out.println(text);
```

1. Hvad blev skrevet ud?
2. Hvorfor blev det ikke `HELLO`?
3. Ret koden, så den skriver `HELLO`.

### Opgave 6 – equals

```java
String a = "Java";
String b = "java";
String c = "Java";
```

Skriv ud, hvad hver af disse giver, og forklar hvorfor:

* `a.equals(b)`
* `a.equals(c)`
* `a.equalsIgnoreCase(b)`

Prøv også `a == c` og `a == b`. Diskutér i gruppen, hvad forskellen er.

---

## Del 2 – Loops og Strings

### Opgave 7 – Ét tegn pr. linje

Lav et program, der skriver hvert tegn i en tekst på sin egen linje.

```text
J
a
v
a
```

### Opgave 8 – Baglæns

Lav et program, der skriver en tekst ud baglæns.

```text
Input:  "Hello"
Output: "olleH"
```

Løs det på to måder:

1. med `System.out.print` inde i loopet
2. ved at bygge en ny `String` op og skrive den ud til sidst

### Opgave 9 – Tæl vokaler

Lav et program, der tæller antallet af vokaler (`a`, `e`, `i`, `o`, `u`) i en tekst.

```text
"programming" indeholder 3 vokaler
```

Hjælp: brug `toLowerCase()` først, så du slipper for at tjekke både store og små bogstaver.

### Opgave 10 – Tæl et bestemt tegn

Lav et program, der tæller, hvor mange gange et bestemt tegn optræder i en tekst.

```java
String text = "mississippi";
char target = 's';
```

```text
's' optræder 4 gange
```

### Opgave 11 – Kun store bogstaver

Lav et program, der skriver alle **store** bogstaver fra en tekst ud.

```text
Input:  "Hello World From Java"
Output: HWFJ
```

Hjælp: `Character.isUpperCase(c)` giver `true`, hvis `c` er et stort bogstav.

### Opgave 12 – Fjern mellemrum

Lav et program, der laver en ny tekst uden mellemrum.

```text
Input:  "Hello big world"
Output: "Hellobigworld"
```

Løs det **uden** at bruge `replace()` – brug et loop.

Løs det derefter **med** `replace()`, og sammenlign de to løsninger.

### Opgave 13 – Palindrom

Et palindrom er et ord, der staves ens forfra og bagfra – f.eks. `regninger` eller `racecar`.

Lav et program, der undersøger, om en tekst er et palindrom.

```text
"racecar" is a palindrom
"hello" is not a palindrom
```

Prøv med: `racecar`, `hello`, `regninger`, `abba`, `a`

### Opgave 14 – Tæl ord

Lav et program, der tæller antallet af ord i en sætning.

```java
String sentence = "Java is a programming language";
```

```text
Sætningen har 5 ord
```

Hjælp: tæl mellemrummene, og læg 1 til. Overvej hvad der sker med to mellemrum i træk.

### Opgave 15 – Initialer

Lav et program, der laver initialer ud fra et fuldt navn.

```text
Input:  "Ada Lovelace King"
Output: "ALK"
```

---

## Del 3 – Opsamling på forløbet

Her skal du bruge alt: variable, betingelser, loops, arrays og Strings.

### Opgave 16 – Karakterstatistik

Lav et array med karakterer:

```java
int[] grades = {12, 7, 4, 10, 2, 12, 7, 0, 10, 4};
```

Programmet skal skrive ud:

* antallet af karakterer
* den højeste karakter
* den laveste karakter
* gennemsnittet (med decimaler!)
* hvor mange der er bestået (02 eller derover)

```text
Antal:       10
Højeste:     12
Laveste:     0
Gennemsnit:  6.8
Bestået:     9
```

> Pas på heltalsdivision, når du beregner gennemsnittet.

### Opgave 17 – Søg i et array

Udvid opgave 16 med en søgefunktion.

Lad brugeren indtaste en karakter med `Scanner`, og skriv ud, om den findes i arrayet – og i så
fald på hvilket index den står første gang.

```text
Indtast en karakter: 10
10 findes på index 3
```

```text
Indtast en karakter: 5
5 findes ikke
```

Brug søgemønsteret med `-1` og `break`.

### Opgave 18 – Menu

Lav et program med denne menu:

```text
1. Tilføj et tal
2. Vis alle tal
3. Vis summen
4. Vis det største tal
5. Afslut

Vælg:
```

Programmet skal blive ved med at vise menuen, indtil brugeren vælger `5`.

Gem tallene i et array med plads til 100 tal, og hold styr på, hvor mange der faktisk er indtastet.

Her skal du bruge: `while`, `switch` eller `if`/`else if`, `Scanner`, array, og de fire mønstre.

### Opgave 19 – Ordanalyse

Lav et program, der beder brugeren om en sætning og derefter skriver:

* antallet af tegn
* antallet af tegn uden mellemrum
* antallet af ord
* antallet af vokaler
* sætningen med store bogstaver
* sætningen baglæns

```text
Indtast en sætning: Java er sjovt

Tegn i alt:        13
Tegn uden mellem:  11
Ord:               3
Vokaler:           4
Store bogstaver:   JAVA ER SJOVT
Baglæns:           tvojs re avaJ
```

### Opgave 20 – Cæsar-kryptering

Lav et program, der forskyder hvert bogstav i en tekst tre pladser frem i alfabetet.

```text
Input:  "abc"
Output: "def"
```

Hjælp: en `char` kan behandles som et tal.

```java
char c = 'a';
char shifted = (char) (c + 3);   // 'd'
```

Håndtér at `z` skal blive til `c` (altså rundt om enden). Du kan nøjes med små bogstaver.

### Ekstra

Lav også en funktion, der dekrypterer igen.

---

## Udfordring 1 – Hangman

Lav et simpelt hangman-spil.

* Programmet har et hemmeligt ord skrevet i koden, f.eks. `"programming"`
* Spilleren gætter ét bogstav ad gangen
* Programmet viser ordet med `_` for de bogstaver, der endnu ikke er gættet
* Spilleren har 8 forsøg

```text
Ordet: ___________
Gæt et bogstav: r
Rigtigt!

Ordet: _r_ _r___ __
Gæt et bogstav: z
Forkert. Du har 7 forsøg tilbage.
```

Her skal du bruge det hele: loops, betingelser, Strings, `charAt`, `contains` og en tæller.

---

## Udfordring 2 – Bogstavstatistik

Lav et program, der tæller, hvor mange gange hvert bogstav i alfabetet optræder i en tekst, og
skriver et lille søjlediagram:

```text
a: ***
b:
c: *
d: **
e: *****
...
```

Hjælp: brug et array med 26 pladser. Bogstavet `'a'` svarer til index `0`:

```java
int index = c - 'a';
```

---

## Hvis du bliver færdig

Gå tilbage og kig på **opgave 10 fra tirsdag** (`Største tal` med fem variable `a` til `e`).

Skriv den om, så tallene ligger i et array, og du bruger et loop. Hvor meget kortere blev den?

Det er en god illustration af, hvorfor vi lærer arrays – og et forvarsel om, hvorfor vi fra mandag
går i gang med **klasser og objekter**.
