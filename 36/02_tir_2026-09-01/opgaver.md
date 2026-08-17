# Opgaver – For-loops og while-loops

I disse opgaver skal du arbejde med `for`-loops, `break`, `continue` og nested loops – og øve dig i
at vælge det rigtige loop til opgaven.

## Kom i gang

Opret et nyt Java-projekt i IntelliJ, eller brug det, du har til undervisningen.

Opret en klasse `Main` med en `main`-metode, og lav løsningerne der. Afprøv dem undervejs.

Nogle opgaver bruger `Scanner`. Husk importen øverst i filen:

```java
import java.util.Scanner;
```

---

## Del 1 – Grundlæggende for-loops

### Opgave 1 – Tæl fra 1 til 10

Lav et `for`-loop, der skriver tallene fra 1 til 10.

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

### Opgave 2 – Tæl fra 0 til 9

Ændr opgave 1, så den skriver `0` til `9` i stedet.

Hvad ændrede du? Der er to forskellige måder at gøre det på – kan du finde begge?

### Opgave 3 – Tæl ned

Lav et `for`-loop, der tæller ned fra 10 til 1, og derefter skriver:

```text
Liftoff!
```

### Opgave 4 – Lige tal

Lav et `for`-loop, der skriver de lige tal fra 2 til 20.

Løs det på to måder:

1. med `i += 2`
2. med `i++` og et `if` inde i loopet

Hvilken synes du er klarest?

### Opgave 5 – Femtabellen

Lav et `for`-loop, der skriver 5-tabellen:

```text
1 * 5 = 5
2 * 5 = 10
3 * 5 = 15
...
10 * 5 = 50
```

---

## Del 2 – Opsamling i en variabel

### Opgave 6 – Summen af 1 til 100

Lav et `for`-loop, der beregner summen af tallene fra 1 til 100.

```text
Summen er 5050
```

Overvej: hvor skal `sum` oprettes – før eller inde i loopet? Prøv begge dele, og se hvad der sker.

### Opgave 7 – Summen af de lige tal

Beregn summen af de lige tal fra 1 til 100.

```text
Summen af de lige tal er 2550
```

### Opgave 8 – Fakultet

Beregn `5!` (5 fakultet), som er `1 * 2 * 3 * 4 * 5`.

```text
5! = 120
```

Hjælp: `sum` starter på `0` når man lægger sammen. Hvad skal startværdien være, når man ganger?

### Opgave 9 – Tæl noget

Lav et program, der tæller, hvor mange tal mellem 1 og 200 der er delelige med både 3 og 5.

Skriv både antallet og selve tallene ud.

### Opgave 10 – Største tal

Lav et program med disse tal skrevet direkte i koden:

```java
int a = 12;
int b = 45;
int c = 7;
int d = 45;
int e = 23;
```

Brug **ikke** et loop endnu – find det største med `if`-sætninger.

> Gem denne opgave. Når vi kommer til arrays, laver vi den om, og så bliver den meget kortere.

---

## Del 3 – break og continue

### Opgave 11 – Stop ved 5

Lav et `for`-loop fra 1 til 10, der stopper helt, når `i` bliver 5.

```text
1
2
3
4
Loopet stoppede
```

### Opgave 12 – Spring 5 over

Lav et `for`-loop fra 1 til 10, der springer tallet 5 over, men fortsætter derefter.

```text
1
2
3
4
6
7
8
9
10
```

### Opgave 13 – Første deleligt med 7

Lav et loop, der finder det **første** tal over 100, der er deleligt med 7 – og stopper der.

```text
Det første tal over 100 der er deleligt med 7 er 105
```

### Opgave 14 – Med og uden continue

Skriv dette program om, så det **ikke** bruger `continue`, men gør præcis det samme:

```java
for (int i = 1; i <= 20; i++) {

    if (i % 3 != 0) {
        continue;
    }

    System.out.println(i);
}
```

Hvilken version synes du er lettest at læse? Diskutér i gruppen.

---

## Del 4 – for eller while?

For hver af opgaverne herunder skal du **først** beslutte, om du vil bruge `for` eller `while`, og
**skrive en kort begrundelse som kommentar** i koden. Løs den derefter.

### Opgave 15 – Ti gange hej

Skriv `Hej` ud ti gange.

### Opgave 16 – Bliv ved indtil 0

Bed brugeren indtaste tal, indtil hun indtaster `0`. Skriv til sidst summen af de indtastede tal
(uden `0`).

```text
Indtast et tal: 5
Indtast et tal: 3
Indtast et tal: 10
Indtast et tal: 0

Summen er: 18
```

### Opgave 17 – Gættespil

Lav et program, hvor brugeren skal gætte et hemmeligt tal mellem 1 og 100.

Programmet skal svare `For lavt` eller `For højt` efter hvert gæt, og til sidst skrive, hvor mange
forsøg der blev brugt.

```java
int secretNumber = 42;
```

### Opgave 18 – Kun tre forsøg

Udvid opgave 17, så brugeren kun har **tre** forsøg. Hvis tallet ikke er gættet, skriver programmet:

```text
Du er løbet tør for forsøg. Tallet var 42
```

Overvej: hvilket loop passer bedst nu, hvor der både er et maksimalt antal forsøg **og** en grund
til at stoppe tidligt?

### Opgave 19 – Skriv om fra while til for

Skriv dette `while`-loop om til et `for`-loop:

```java
int i = 100;

while (i >= 0) {
    System.out.println(i);
    i -= 10;
}
```

### Opgave 20 – Skriv om fra for til while

Skriv dette `for`-loop om til et `while`-loop:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Række " + i);
}
```

---

## Del 5 – Nested loops

### Opgave 21 – Rektangel af stjerner

Lav et program, der tegner et rektangel på 4 rækker og 6 kolonner:

```text
******
******
******
******
```

### Opgave 22 – Trekant

Lav et program, der tegner denne trekant:

```text
*
**
***
****
*****
```

### Opgave 23 – Omvendt trekant

Lav et program, der tegner denne:

```text
*****
****
***
**
*
```

### Opgave 24 – Højrestillet trekant

Sværere. Lav denne:

```text
    *
   **
  ***
 ****
*****
```

Hjælp: hver række består af **mellemrum** efterfulgt af **stjerner**. Hvor mange af hver, når du er
i række `i`?

### Opgave 25 – Den lille tabel

Lav et program, der skriver hele den lille tabel (1 til 10):

```text
1	2	3	4	5	6	7	8	9	10
2	4	6	8	10	12	14	16	18	20
3	6	9	12	15	18	21	24	27	30
...
```

Brug `\t` mellem tallene.

### Opgave 26 – Tæl gennemløbene

Lav et program med to nested loops, hvor det ydre kører 4 gange og det indre 5 gange.

Tæl med en variabel, hvor mange gange den inderste kode bliver kørt, og skriv tallet ud til sidst.

Var det, hvad du forventede?

---

## Del 6 – Find fejlen

### Opgave 27

```java
for (int i = 0; i < 5; i++);
{
    System.out.println("Hej");
}
```

1. Hvad skriver programmet ud?
2. Hvorfor?
3. Ret fejlen.

### Opgave 28

```java
for (int i = 1; i <= 10; i--) {
    System.out.println(i);
}
```

1. Hvad sker der, når du kører programmet?
2. Hvordan stopper du det?
3. Ret fejlen på to forskellige måder.

### Opgave 29

```java
for (int i = 1; i <= 5; i++) {
    int sum = 0;
    sum += i;
}
```

Programmet skulle beregne summen af 1 til 5. Det virker ikke.

1. Hvad er problemet?
2. Ret det.
3. Skriv summen ud.

### Opgave 30

```java
int i = 1;

while (i <= 10) {

    if (i % 2 == 0) {
        continue;
    }

    System.out.println(i);
    i++;
}
```

1. Hvad sker der, når du kører programmet?
2. Hvorfor er `continue` farlig lige her?
3. Ret koden.

---

## Udfordring 1 – Primtal

Lav et program, der undersøger, om et tal er et primtal.

```java
int number = 29;
```

Output:

```text
29 is a prime number
```

Hjælp: et tal er et primtal, hvis det kun kan divideres med 1 og sig selv. Prøv at dividere med
alle tal fra 2 op til `number - 1` og se, om nogen går op.

### Ekstra

* Kan du gøre programmet hurtigere ved kun at gå op til `number / 2`?
* Eller op til kvadratroden af `number`? (`Math.sqrt(number)`)
* Udvid programmet, så det skriver alle primtal mellem 1 og 100.

---

## Udfordring 2 – FizzBuzz

Skriv tallene fra 1 til 100 ud, men:

* er tallet deleligt med 3, skriv `Fizz` i stedet for tallet
* er tallet deleligt med 5, skriv `Buzz` i stedet
* er det deleligt med både 3 og 5, skriv `FizzBuzz`

```text
1
2
Fizz
4
Buzz
Fizz
7
...
14
FizzBuzz
16
```

> Denne opgave er en klassiker til jobsamtaler. Pas især på rækkefølgen af dine betingelser.

---

## Udfordring 3 – Multiplikationstabel med overskrifter

Udvid opgave 25, så tabellen får overskrifter og streger:

```text
    |   1   2   3   4   5
----+--------------------
  1 |   1   2   3   4   5
  2 |   2   4   6   8  10
  3 |   3   6   9  12  15
  4 |   4   8  12  16  20
  5 |   5  10  15  20  25
```

Hjælp: `System.out.printf("%4d", tal)` skriver et tal ud med fast bredde på 4 tegn.

---

## Udfordring 4 – Terningespil

Lav et program, der kaster to terninger 1000 gange og tæller, hvor mange gange hver sum (2 til 12)
forekommer.

Til at slå en terning kan du bruge:

```java
import java.util.Random;

Random random = new Random();

int die = random.nextInt(6) + 1;
```

Skriv resultatet ud som et lille søjlediagram:

```text
 2: ***
 3: ******
 4: *********
 5: ************
 6: ***************
 7: *****************
 8: **************
 ...
```

Hjælp: du får brug for en måde at gemme 11 tal på. Indtil vi lærer om arrays, kan du klare dig med
elleve variable – eller vente med denne opgave til efter arrays i morgen.
