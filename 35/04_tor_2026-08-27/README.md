# Logiske operatorer. Betingelser og beslutninger

## Beskrivelse

I denne lektion skal programmet for første gang **træffe en beslutning**.

Indtil nu har vores programmer kørt fra øverste til nederste linje, hver eneste gang. Nu lærer vi
at få programmet til at vælge mellem forskellige veje afhængigt af, hvad der er sandt.

Vi arbejder med `boolean`-værdier, sammenligningsoperatorer, `if`, `else if`, `else` og de logiske
operatorer `&&`, `||` og `!`.

> **Bemærk:** Vi bruger endnu ikke `Scanner` til at læse input fra brugeren – det kommer i morgen.
> I dag sætter vi værdierne direkte i koden og ændrer dem manuelt for at afprøve de forskellige
> tilfælde.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* forklare hvad en `boolean` er, og at den kun kan være `true` eller `false`
* bruge sammenligningsoperatorerne `==`, `!=`, `<`, `>`, `<=`, `>=`
* kende forskel på `=` og `==`
* skrive en `if`-sætning
* bruge `else` og `else if`
* kombinere betingelser med `&&` (og), `||` (eller) og `!` (ikke)
* forklare hvornår `&&` og `||` giver `true`
* skrive og læse indlejrede (*nested*) `if`-sætninger
* forudsige resultatet af et boolesk udtryk uden at køre koden

## Se disse videoer før undervisningen:

[if statements](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=1h9m0s) (til: 01:22:28)
[nested if statements](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=2h3m47s) (til: 02:10:20)
[logical operators](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=3h9m58s) (til: 03:21:23)

## Læs nedenstående før undervisningen

Afprøv gerne eksemplerne i IntelliJ, mens du læser.

Brug samme fremgangsmåde som de foregående dage: opret en klasse `Main` med en `main`-metode, og
skriv koden derinde.

```java
public class Main {

    public static void main(String[] args) {

    }
}
```

---

### Alt starter med sandt eller falsk

Du har allerede mødt datatypen `boolean`. Den kan kun indeholde to værdier:

```java
boolean isRaining = true;
boolean isSunny = false;
```

Der findes ikke "måske". En `boolean` er enten `true` eller `false`.

Det lyder småt, men det er præcis det, der gør computeren i stand til at træffe beslutninger. Hele
resten af dagens emne bygger på denne ene ting.

---

### Sammenligningsoperatorer

Vi laver som regel ikke `boolean`-værdier i hånden. Vi **beregner** dem ved at sammenligne noget.

| Operator | Betydning | Eksempel | Resultat |
| --- | --- | --- | --- |
| `==` | er lig med | `5 == 5` | `true` |
| `!=` | er ikke lig med | `5 != 3` | `true` |
| `<` | mindre end | `3 < 5` | `true` |
| `>` | større end | `3 > 5` | `false` |
| `<=` | mindre end eller lig med | `5 <= 5` | `true` |
| `>=` | større end eller lig med | `3 >= 5` | `false` |

Et udtryk med en sammenligningsoperator **er** en `boolean`:

```java
int age = 20;

boolean isAdult = age >= 18;

System.out.println(isAdult);
```

Output:

```text
true
```

Læg mærke til, at `age >= 18` ikke er et spørgsmål, vi stiller. Det er en **værdi** – på præcis
samme måde som `5 + 3` er en værdi.

Du kan udskrive en sammenligning direkte:

```java
int temperature = 12;

System.out.println(temperature > 20);
System.out.println(temperature < 20);
System.out.println(temperature == 12);
```

Output:

```text
false
true
true
```

---

### `=` og `==` er ikke det samme

Det her er en af de klassiske begynderfejl, og den bliver ved med at drille længe:

```java
int age = 20;    // tildeling: put 20 ind i age
age == 20        // sammenligning: er age lig med 20?
```

* Ét lighedstegn `=` **sætter** en værdi.
* To lighedstegn `==` **spørger**, om to værdier er ens.

Hvis du skriver `=`, hvor du mente `==`, får du enten en fejl fra compileren eller – værre – et
program, der stille og roligt gør noget andet, end du troede.

> **Huskeregel:** `=` er en kommando. `==` er et spørgsmål.

---

### `if` – gør noget, hvis noget er sandt

Nu kan vi bruge vores `boolean` til noget.

Grundformen er:

```java
if (betingelse) {
    // kode der kun køres hvis betingelsen er true
}
```

Eksempel:

```java
int age = 20;

if (age >= 18) {
    System.out.println("You are an adult");
}
```

Output:

```text
You are an adult
```

Prøv at ændre `age` til `15` og kør igen. Nu bliver der ikke skrevet noget. Betingelsen var
`false`, så koden mellem `{ }` blev sprunget over.

Bemærk:

* Betingelsen står i **runde parenteser**.
* Koden, der skal køres, står i **krøllede parenteser** `{ }`.
* Der er **ikke** semikolon efter `if (...)`.

Dette er en klassisk fejl:

```java
if (age >= 18);          // ← semikolon her er en fejl!
{
    System.out.println("You are an adult");
}
```

Her bliver teksten skrevet ud **altid**, uanset alderen. Semikolonet afslutter `if`-sætningen, og
blokken bagefter bliver bare almindelig kode.

---

### `else` – ellers gør noget andet

Ofte vil vi gøre én ting, hvis betingelsen er sand, og noget andet, hvis den er falsk:

```java
int age = 15;

if (age >= 18) {
    System.out.println("You are an adult");
}
else {
    System.out.println("You are a minor");
}
```

Output:

```text
You are a minor
```

Præcis **én** af de to blokke bliver kørt. Aldrig begge, aldrig ingen.

---

### `else if` – flere muligheder

Hvis der er mere end to muligheder, kan vi kæde dem sammen:

```java
int grade = 78;

if (grade >= 90) {
    System.out.println("Grade: A");
}
else if (grade >= 80) {
    System.out.println("Grade: B");
}
else if (grade >= 70) {
    System.out.println("Grade: C");
}
else {
    System.out.println("Grade: F");
}
```

Output:

```text
Grade: C
```

**Rækkefølgen betyder alt.** Java prøver betingelserne oppefra og ned og stopper ved den første,
der er `true`. Resten bliver slet ikke undersøgt.

Se hvad der sker, hvis vi vender rækkefølgen om:

```java
int grade = 95;

if (grade >= 70) {
    System.out.println("Grade: C");     // ← denne rammer først!
}
else if (grade >= 80) {
    System.out.println("Grade: B");
}
else if (grade >= 90) {
    System.out.println("Grade: A");
}
```

Output:

```text
Grade: C
```

Selvom karakteren er 95, får vi `C`. Fordi `95 >= 70` er sandt, og så ser Java ikke længere.

> Når du laver en kæde af `else if` med tal, så gå enten fra størst til mindst eller fra mindst til
> størst. Ikke i vilkårlig rækkefølge.

---

### Det er kun ét spor

Det er værd at være helt skarp på: i en `if` / `else if` / `else`-kæde bliver der kørt **højst én**
blok.

```java
int number = 5;

if (number > 0) {
    System.out.println("positive");
}
else if (number > 3) {
    System.out.println("greater than three");
}
```

Output:

```text
positive
```

`number > 3` er også sandt – men vi kommer aldrig derhen.

Hvis du vil have begge udskrifter, skal det være to selvstændige `if`-sætninger:

```java
int number = 5;

if (number > 0) {
    System.out.println("positive");
}

if (number > 3) {
    System.out.println("greater than three");
}
```

Output:

```text
positive
greater than three
```

---

### Logiske operatorer

Nogle gange afhænger en beslutning af **flere** ting på én gang.

| Operator | Navn | Giver `true` når ... |
| --- | --- | --- |
| `&&` | og (AND) | **begge** sider er `true` |
| `\|\|` | eller (OR) | **mindst én** side er `true` |
| `!` | ikke (NOT) | udtrykket er `false` |

#### `&&` – begge skal være sande

```java
int age = 25;
boolean hasLicense = true;

if (age >= 18 && hasLicense) {
    System.out.println("You may drive");
}
else {
    System.out.println("You may not drive");
}
```

Output:

```text
You may drive
```

Hvis bare én af de to ting ikke passer, falder hele udtrykket til `false`.

Sandhedstabel for `&&`:

| venstre | højre | `venstre && højre` |
| --- | --- | --- |
| `true` | `true` | `true` |
| `true` | `false` | `false` |
| `false` | `true` | `false` |
| `false` | `false` | `false` |

#### `||` – mindst én skal være sand

```java
int temperature = 35;

if (temperature < 0 || temperature > 30) {
    System.out.println("Extreme weather");
}
```

Output:

```text
Extreme weather
```

Sandhedstabel for `||`:

| venstre | højre | `venstre \|\| højre` |
| --- | --- | --- |
| `true` | `true` | `true` |
| `true` | `false` | `true` |
| `false` | `true` | `true` |
| `false` | `false` | `false` |

> Bemærk: `||` i programmering betyder "den ene, den anden, **eller begge**". Det er ikke det
> "enten-eller", vi ofte mener i daglig tale.

#### `!` – vend det om

`!` vender en `boolean` på hovedet:

```java
boolean isRaining = false;

if (!isRaining) {
    System.out.println("Let's go outside");
}
```

Output:

```text
Let's go outside
```

`!isRaining` læses som "ikke isRaining", altså "hvis det ikke regner".

---

### Et interval

En meget almindelig brug af `&&` er at tjekke, om et tal ligger i et interval:

```java
int number = 7;

if (number >= 1 && number <= 10) {
    System.out.println("The number is between 1 and 10");
}
```

Det her virker **ikke** i Java, selvom det ser rigtigt ud matematisk:

```java
if (1 <= number <= 10) {     // ← fejl
```

Java kan ikke sammenligne tre ting på én gang. Du skal skrive to sammenligninger og binde dem
sammen med `&&`.

---

### At skrive betingelser pænt

Disse to gør præcis det samme:

```java
if (isStudent == true) {
    ...
}
```

```java
if (isStudent) {
    ...
}
```

Den nederste er den, man normalt skriver. `isStudent` **er** allerede en `boolean` – vi behøver
ikke spørge, om `true` er lig med `true`.

Tilsvarende:

```java
if (isStudent == false) { ... }
```

skrives normalt:

```java
if (!isStudent) { ... }
```

Det er også derfor, det betaler sig at give `boolean`-variable navne, der lyder som et
ja/nej-spørgsmål:

```java
boolean isAdult;
boolean hasLicense;
boolean isEmpty;
boolean canDrive;
```

Så kommer `if (canDrive)` til at læse næsten som almindelig tekst.

---

### Nested if – en `if` inden i en `if`

Nogle gange giver det først mening at stille det andet spørgsmål, når det første er besvaret:

```java
boolean hasLicense = true;
int age = 20;

if (hasLicense) {

    if (age >= 18) {
        System.out.println("You may drive");
    }
    else {
        System.out.println("You are too young, license or not");
    }

}
else {
    System.out.println("You need a license first");
}
```

Her spørger vi først om kørekort. Kun hvis der er et kørekort, spørger vi om alderen.

Mange indlejrede `if`-sætninger kan ofte skrives om med `&&`:

```java
if (hasLicense && age >= 18) {
    System.out.println("You may drive");
}
```

Den korte version er lettere at læse – men den kan ikke give tre forskellige beskeder. **Vælg den
form, der bedst udtrykker det, du mener.** Hvis du kun har brug for ét ja/nej-svar, så brug `&&`.
Hvis der er forskellige svar undervejs, så er nesting ofte klarere.

> Bliver koden mere end to-tre niveauer dyb, er det næsten altid et tegn på, at den bør skrives om.

---

### Bonus: den ternære operator

Der findes en kort form til de allersimpleste valg:

```java
int age = 20;

String status = (age >= 18) ? "adult" : "minor";

System.out.println(status);
```

Output:

```text
adult
```

Det svarer til:

```java
String status;

if (age >= 18) {
    status = "adult";
}
else {
    status = "minor";
}
```

Formen er:

```text
betingelse ? værdiHvisSand : værdiHvisFalsk
```

Brug den kun, når den gør koden **lettere** at læse. Du behøver ikke bruge den, men det er godt at
kunne genkende den.

---

### Kan du forudsige resultatet?

Prøv at svare **uden at køre koden**. Skriv dine svar ned, og tjek dem bagefter.

#### Eksempel 1

```java
int a = 5;
int b = 10;

System.out.println(a > b);
System.out.println(a < b);
System.out.println(a == b);
System.out.println(a != b);
```

#### Eksempel 2

```java
boolean x = true;
boolean y = false;

System.out.println(x && y);
System.out.println(x || y);
System.out.println(!x);
System.out.println(!y);
```

#### Eksempel 3

```java
int number = 4;

if (number > 10) {
    System.out.println("big");
}
else if (number > 2) {
    System.out.println("medium");
}
else {
    System.out.println("small");
}
```

#### Eksempel 4

```java
int number = 15;

if (number > 10) {
    System.out.println("A");
}

if (number > 5) {
    System.out.println("B");
}

if (number > 20) {
    System.out.println("C");
}
```

#### Eksempel 5

```java
int age = 17;
boolean hasPermission = true;

if (age >= 18 || hasPermission) {
    System.out.println("Allowed");
}
else {
    System.out.println("Not allowed");
}
```

#### Eksempel 6

```java
int x = 5;

if (x = 5) {
    System.out.println("five");
}
```

> Hvad sker der her? Kør den, og læs fejlmeddelelsen grundigt.

---

## Det vigtigste at tage med

Efter denne forberedelse skal du især kunne:

* forklare at en `boolean` kun kan være `true` eller `false`
* bruge `==`, `!=`, `<`, `>`, `<=`, `>=` til at beregne en `boolean`
* forklare forskellen på `=` og `==`
* skrive en `if`-sætning med `{ }` og uden semikolon efter betingelsen
* bruge `else` og `else if`, og forklare hvorfor **rækkefølgen** betyder noget
* forklare at der kun køres **én** blok i en `if` / `else if` / `else`-kæde
* bruge `&&`, `||` og `!` og udfylde deres sandhedstabeller
* tjekke om et tal ligger i et interval med `&&`
* skrive `if (isStudent)` frem for `if (isStudent == true)`
* læse en indlejret `if`-sætning
* forudsige resultatet af et boolesk udtryk uden at køre koden

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md)
