# Loops og Strings. Repetition og opsamling på forløbet

## Beskrivelse

I dag afslutter vi det første forløb, **Introduktion til programmering**.

Vi lærer at arbejde med tekst: hvordan man finder ud af, hvor lang en `String` er, hvordan man
henter enkelte tegn ud af den, og hvordan man løber en tekst igennem med et loop.

Derefter samler vi op på alt det, vi har været igennem i uge 35 og 36 – variable, datatyper,
operatorer, betingelser, loops og arrays – og sætter det sammen i nogle lidt større opgaver.

Fra på mandag går vi i gang med **klasser og objekter** og det første projekt.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* bruge `length()`, `charAt()`, `substring()`, `indexOf()`, `toUpperCase()` og `contains()`
* forklare at et tegn i en `String` findes på et **index**, og at det første index er `0`
* løbe en `String` igennem med et `for`-loop
* sammenligne tekst korrekt med `.equals()` og forklare, hvorfor `==` ikke duer
* bygge en ny `String` op i et loop
* kombinere loops, betingelser, arrays og Strings i den samme opgave

## Se disse videoer før undervisningen:

[string methods](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=2h10m20s) (til: 02:18:55)
[substrings](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=2h18m55s) (til: 02:27:00)

## Læs nedenstående før undervisningen

---

### En String er en række af tegn

![Sættekasser med løse blytyper på et bogtrykkeri](images/saettekasse.jpg)

*Før computeren blev tekst sat i hånden, ét bogstav ad gangen, fra kasser som disse. Ordet
"sætte" hænger stadig ved. En `String` er præcis det samme: en række enkelttegn i en bestemt
rækkefølge.*

Du har brugt `String` siden dag ét:

```java
String name = "Anna";
```

Det nye i dag er, at en `String` ikke bare er én ting. Den er en **række af enkelte tegn**, og vi
kan komme til hvert af dem.

Tegnene er nummererede. Nummeret kaldes et **index**, og det starter ved `0`:

```text
String:   A   n   n   a
index:    0   1   2   3
```

Det er præcis samme princip som i et array. Første element har index `0`.

---

### `length()` – hvor langt er det?

```java
String name = "Anna";

System.out.println(name.length());
```

Output:

```text
4
```

Bemærk parenteserne: `name.length()`. På et array hedder det `array.length` **uden** parenteser.
Det er en irriterende lille forskel, som alle støder på:

```java
String text = "Anna";
int[] numbers = {1, 2, 3};

text.length()      // String: metode, med parenteser
numbers.length     // array: felt, uden parenteser
```

> **Vigtigt:** Det sidste gyldige index er `length() - 1`. En `String` med længde 4 har indexene
> 0, 1, 2 og 3. Der er **ikke** noget index 4.

---

### `charAt()` – hent ét tegn

```java
String name = "Anna";

System.out.println(name.charAt(0));
System.out.println(name.charAt(3));
```

Output:

```text
A
a
```

`charAt()` returnerer en `char` – ikke en `String`. Derfor:

```java
char firstLetter = name.charAt(0);
```

Går du uden for teksten, får du en fejl, når programmet kører:

```java
System.out.println(name.charAt(4));
```

```text
Exception in thread "main" java.lang.StringIndexOutOfBoundsException
```

Den fejl kommer du til at se mange gange. Den betyder altid det samme: du bad om et index, der
ikke findes.

---

### Løb en String igennem

Nu kan vi kombinere det med et `for`-loop:

```java
String name = "Anna";

for (int i = 0; i < name.length(); i++) {
    System.out.println(name.charAt(i));
}
```

Output:

```text
A
n
n
a
```

Læg mærke til betingelsen: `i < name.length()`, **ikke** `i <= name.length()`.

Fordi indexene går fra `0` til `length() - 1`, ville `<=` give en fejl i sidste gennemløb. Det er
den absolut hyppigste loop-fejl, og den har et navn: en *off-by-one*-fejl.

> **Mønsteret** `for (int i = 0; i < noget.length(); i++)` kommer du til at skrive hundredvis af
> gange. Lær det udenad nu.

Baglæns er lige så let:

```java
String name = "Anna";

for (int i = name.length() - 1; i >= 0; i--) {
    System.out.print(name.charAt(i));
}
```

Output:

```text
annA
```

---

### `substring()` – klip en bid ud

```java
String text = "Hello world";

System.out.println(text.substring(6));
System.out.println(text.substring(0, 5));
```

Output:

```text
world
Hello
```

Med ét argument: "fra dette index og resten ud".
Med to argumenter: "fra det første index **til, men ikke med**, det andet".

Det sidste er værd at dvæle ved:

```text
"Hello world"
 01234567890
      ↑
substring(0, 5)  →  index 0, 1, 2, 3, 4   →  "Hello"
```

Index `5` er **ikke** med. Det virker mærkeligt første gang, men det har en fordel: længden af
resultatet er altid `slut - start`. `5 - 0 = 5` tegn.

---

### `indexOf()` – hvor står det?

```java
String text = "Hello world";

System.out.println(text.indexOf("world"));
System.out.println(text.indexOf("o"));
System.out.println(text.indexOf("z"));
```

Output:

```text
6
4
-1
```

`indexOf` returnerer index for den **første** forekomst – eller `-1`, hvis teksten slet ikke findes.

`-1` er en meget almindelig måde at sige "ikke fundet" på. Tjek altid for den:

```java
int position = text.indexOf("world");

if (position != -1) {
    System.out.println("Fundet på index " + position);
}
else {
    System.out.println("Ikke fundet");
}
```

---

### Flere nyttige metoder

```java
String text = "  Hello World  ";

System.out.println(text.toUpperCase());      // "  HELLO WORLD  "
System.out.println(text.toLowerCase());      // "  hello world  "
System.out.println(text.trim());             // "Hello World"
System.out.println(text.contains("World"));  // true
System.out.println(text.isEmpty());          // false
System.out.println("Hello".replace("l", "L")); // "HeLLo"
```

| Metode | Gør hvad |
| --- | --- |
| `length()` | Antal tegn |
| `charAt(i)` | Tegnet på index `i` |
| `substring(a)` | Fra index `a` og resten |
| `substring(a, b)` | Fra `a` til (men ikke med) `b` |
| `indexOf(s)` | Index for første forekomst, ellers `-1` |
| `contains(s)` | `true` hvis teksten indeholder `s` |
| `toUpperCase()` | Alt med store bogstaver |
| `toLowerCase()` | Alt med små bogstaver |
| `trim()` | Fjerner mellemrum i begge ender |
| `replace(a, b)` | Erstatter alle `a` med `b` |
| `equals(s)` | `true` hvis teksterne er ens |
| `equalsIgnoreCase(s)` | Som `equals`, men er ligeglad med store/små |
| `isEmpty()` | `true` hvis teksten er tom |

---

### En String kan ikke ændres

Det her overrasker mange:

```java
String text = "Hello";

text.toUpperCase();

System.out.println(text);
```

Output:

```text
Hello
```

Ikke `HELLO`. En `String` i Java kan **ikke ændres**. `toUpperCase()` laver en **ny** String og
returnerer den – den originale bliver liggende uændret.

Du skal gemme resultatet:

```java
String text = "Hello";

text = text.toUpperCase();

System.out.println(text);
```

Output:

```text
HELLO
```

Det gælder alle String-metoderne: `trim()`, `replace()`, `substring()` og resten. De **returnerer**
noget nyt. De ændrer ikke det, du kalder dem på.

---

### Sammenlign tekst med `.equals()`

Det her er vigtigt, og det er en fælde, næsten alle falder i:

```java
String a = "hello";
String b = "hello";

System.out.println(a == b);         // kan være true ...
```

```java
String c = new String("hello");

System.out.println(a == c);         // ... men er false her
```

`==` sammenligner, om det er **det samme objekt** – ikke om teksten er ens. Til tekst skal du
altid bruge `.equals()`:

```java
System.out.println(a.equals(c));    // true
```

> **Regel indtil videre:** Brug `==` til tal (`int`, `double`) og `boolean`.
> Brug `.equals()` til `String`.
>
> Vi kommer til at forstå *hvorfor*, når vi arbejder med objekter og referencer i uge 37 og 39. For
> nu er reglen nok.

Skal du være ligeglad med store og små bogstaver:

```java
String answer = "JA";

if (answer.equalsIgnoreCase("ja")) {
    System.out.println("Du sagde ja");
}
```

---

### Byg en String op i et loop

Man kan lægge tekst sammen med `+`:

```java
String result = "";

for (int i = 1; i <= 5; i++) {
    result = result + i;
}

System.out.println(result);
```

Output:

```text
12345
```

Bemærk startværdien: `""` – en tom String. Det er det samme mønster som `sum = 0` ved tal.

Man kan også bruge `+=`:

```java
result += i;
```

Sådan vender man en tekst om:

```java
String text = "Hello";
String reversed = "";

for (int i = text.length() - 1; i >= 0; i--) {
    reversed += text.charAt(i);
}

System.out.println(reversed);
```

Output:

```text
olleH
```

---

### Tælle noget i en tekst

Kombinationen loop + `if` + tæller er det samme mønster som med tal:

```java
String text = "programming";
int count = 0;

for (int i = 0; i < text.length(); i++) {

    if (text.charAt(i) == 'm') {
        count++;
    }
}

System.out.println("Der er " + count + " m'er");
```

Output:

```text
Der er 2 m'er
```

Bemærk at vi sammenligner med `==` her – fordi `charAt()` giver en `char`, som er et tal-agtigt
primitiv, ikke en `String`. Og bemærk enkelte anførselstegn: `'m'` er en `char`, `"m"` er en
`String`.

---

## Repetition – hvad har vi været igennem?

Brug denne oversigt til at tjekke dig selv. Er der noget, du ikke er sikker på, så er i dag dagen
til at spørge.

### Uge 35

| Dag | Emne | Kan du ...? |
| --- | --- | --- |
| ma 24-08 | Introdag, studiegrupper | – |
| ti 25-08 | Installation, Java i Notepad | forklare hvad `javac` og `java` gør |
| on 26-08 | Variable, datatyper, aritmetik | vælge mellem `int` og `double`, og forklare heltalsdivision |
| to 27-08 | [Logiske operatorer, betingelser](../../35/04_tor_2026-08-27/README.md) | skrive en `if`/`else if`/`else`-kæde og bruge `&&`, `\|\|`, `!` |
| fr 28-08 | I/O: Scanner, print, Git-bruger | læse et tal og en tekst fra brugeren |

### Uge 36

| Dag | Emne | Kan du ...? |
| --- | --- | --- |
| ma 31-08 | [While-loops](../01_man_2026-08-31/README.md) | skrive et `while`-loop og undgå uendelige loops |
| ti 01-09 | [For-loops](../02_tir_2026-09-01/README.md) | skrive et `for`-loop og et nested loop |
| on 02-09 | [Arrays](../03_ons_2026-09-02/README.md) | oprette et array og løbe det igennem |
| fr 04-09 | Loops og Strings, opsamling | det hele på én gang |

### De fire mønstre du skal kunne udenad

Næsten alt, vi har lavet indtil nu, er en variation over disse fire:

**1. Gennemløb**

```java
for (int i = 0; i < n; i++) {
    // gør noget med i
}
```

**2. Opsamling**

```java
int sum = 0;                    // startværdi FØR loopet

for (int i = 0; i < n; i++) {
    sum += ...;
}
```

**3. Tælling under en betingelse**

```java
int count = 0;

for (int i = 0; i < n; i++) {

    if (betingelse) {
        count++;
    }
}
```

**4. Søgning**

```java
int foundAt = -1;               // -1 betyder "ikke fundet"

for (int i = 0; i < n; i++) {

    if (fundet) {
        foundAt = i;
        break;
    }
}
```

Kan du de fire, kan du overraskende meget.

---

### Kan du forudsige resultatet?

#### Eksempel 1

```java
String text = "Java";

System.out.println(text.length());
System.out.println(text.charAt(0));
System.out.println(text.charAt(text.length() - 1));
```

#### Eksempel 2

```java
String text = "Hello world";

System.out.println(text.substring(0, 5));
System.out.println(text.substring(6));
System.out.println(text.indexOf("o"));
System.out.println(text.indexOf("q"));
```

#### Eksempel 3

```java
String text = "hello";

text.toUpperCase();

System.out.println(text);
```

#### Eksempel 4

```java
String a = "abc";
String b = "ABC";

System.out.println(a.equals(b));
System.out.println(a.equalsIgnoreCase(b));
```

#### Eksempel 5

```java
String text = "abc";

for (int i = 0; i <= text.length(); i++) {
    System.out.println(text.charAt(i));
}
```

> Hvad går galt her? Hvad hedder fejlen?

#### Eksempel 6

```java
String result = "";

for (int i = 3; i >= 1; i--) {
    result += i;
}

System.out.println(result);
```

---

## Det vigtigste at tage med

* en `String` er en række af tegn med index fra `0` til `length() - 1`
* `text.length()` med parenteser – `array.length` uden
* `charAt(i)` giver en `char`; `substring(a, b)` tager ikke `b` med
* `indexOf` giver `-1`, når noget ikke findes
* String-metoder **ændrer ikke** originalen – de returnerer noget nyt
* sammenlign tekst med `.equals()`, ikke `==`
* mønsteret `for (int i = 0; i < text.length(); i++)`
* de fire mønstre: gennemløb, opsamling, tælling, søgning

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md)
