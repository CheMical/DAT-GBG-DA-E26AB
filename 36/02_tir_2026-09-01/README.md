# For-loops og while-loops

## Beskrivelse

I går arbejdede vi med `while`-loops. I dag lærer vi `for`-loopet.

Et `for`-loop kan præcis det samme som et `while`-loop – men det samler de tre ting, der styrer en
gentagelse (**start**, **betingelse** og **ændring**), på én linje. Det gør koden kortere og
lettere at læse, når vi på forhånd ved, hvor mange gange noget skal gentages.

Vi ser også på `break` og `continue`, og på hvad der sker, når man putter et loop inde i et andet.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* skrive et `for`-loop med initialisering, betingelse og ændring
* forklare i hvilken rækkefølge de tre dele af et `for`-loop udføres
* tælle op, ned og i spring med et `for`-loop
* vælge mellem `for` og `while` ud fra opgaven
* bruge `break` til at afbryde et loop
* bruge `continue` til at springe et gennemløb over
* skrive et loop inde i et andet loop (*nested loops*)
* forudsige hvor mange gange et nested loop kører i alt

## Se disse videoer før undervisningen:

[for loops](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=3h43m33s) (til: 03:53:33)
[break & continue](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=3h53m33s) (til: 03:55:45)
[nested loops](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=3h55m45s) (til: 04:04:27)

## Læs nedenstående før undervisningen

Afprøv gerne eksemplerne i IntelliJ, mens du læser.

---

### Kort repetition: while

Sådan så et `while`-loop ud i går:

```java
int number = 1;             // start

while (number <= 5) {       // betingelse
    System.out.println(number);

    number++;               // ændring
}
```

Output:

```text
1
2
3
4
5
```

De tre dele, der styrer loopet, ligger tre forskellige steder:

* **start** står *før* loopet
* **betingelse** står *i* `while (...)`
* **ændring** står *inde i* loopet, typisk nederst

Det virker fint – men de tre ting hører logisk sammen, og de er spredt ud. Og glemmer man
ændringen, kører loopet for evigt.

---

### For-loopet samler de tre dele

Et `for`-loop skriver præcis de samme tre ting, men på én linje:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

Output:

```text
1
2
3
4
5
```

Nøjagtig samme resultat som `while`-loopet ovenfor – men nu står start, betingelse og ændring
sammen, hvor man kan se dem alle tre på én gang.

Grundformen er:

```java
for (start; betingelse; ændring) {
    // kode der skal gentages
}
```

De tre dele er adskilt af **semikolon**, ikke komma.

---

### Rækkefølgen – hvad sker der hvornår?

Det her er værd at få helt på plads. Se på:

```java
for (int i = 1; i <= 3; i++) {
    System.out.println(i);
}
```

Java gør følgende:

1. `int i = 1` – **kun én gang**, allerførst
2. `i <= 3` → `true` → kør koden i loopet → udskriv `1`
3. `i++` → `i` er nu `2`
4. `i <= 3` → `true` → udskriv `2`
5. `i++` → `i` er nu `3`
6. `i <= 3` → `true` → udskriv `3`
7. `i++` → `i` er nu `4`
8. `i <= 3` → `false` → **stop**

Læg mærke til to ting:

* **Betingelsen tjekkes før hvert gennemløb** – også allerførste gang.
* **Ændringen sker efter koden i loopet** – ikke før.

Det betyder, at hvis betingelsen er falsk fra starten, kører loopet **nul gange**:

```java
for (int i = 10; i < 5; i++) {
    System.out.println("Hej");
}
```

Her bliver der ikke skrevet noget som helst.

---

### Hvorfor hedder den `i`?

Tælleren i et `for`-loop hedder traditionelt `i` – for *index* eller *iteration*. Bruger man to
loops inde i hinanden, hedder den næste `j`, og så `k`.

Det er en af de få steder, hvor et enkelt bogstav er et godt variabelnavn, fordi alle
programmører genkender det med det samme.

Men hvis tælleren betyder noget bestemt, så giv den et rigtigt navn:

```java
for (int year = 2020; year <= 2026; year++) {
    System.out.println(year);
}
```

---

### Tælleren findes kun inde i loopet

Bemærk hvor `i` bliver oprettet:

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}

System.out.println(i);   // ← fejl! i findes ikke her
```

Når `i` erklæres inde i `for (...)`, findes den kun så længe loopet kører. Bagefter er den væk.

Det er som regel en fordel – men har du brug for værdien bagefter, skal du oprette variablen før
loopet:

```java
int i;

for (i = 1; i <= 5; i++) {
    System.out.println(i);
}

System.out.println("Loopet stoppede med i = " + i);
```

---

### Tæl ned

Ændringen behøver ikke være `i++`:

```java
for (int i = 5; i > 0; i--) {
    System.out.println(i);
}

System.out.println("Liftoff!");
```

Output:

```text
5
4
3
2
1
Liftoff!
```

Bemærk at betingelsen også skal vendes om: når vi tæller ned, er det `i > 0` og ikke `i <= 5`.

### Tæl i spring

```java
for (int i = 0; i <= 20; i += 5) {
    System.out.println(i);
}
```

Output:

```text
0
5
10
15
20
```

### De lige tal

```java
for (int i = 2; i <= 10; i += 2) {
    System.out.println(i);
}
```

Output:

```text
2
4
6
8
10
```

---

### For eller while?

Begge kan alt, hvad den anden kan. Men de er gode til hver sin slags opgave:

| Brug `for` når ... | Brug `while` når ... |
| --- | --- |
| du **ved på forhånd**, hvor mange gange | du **ikke ved**, hvor mange gange |
| du tæller | du venter på, at noget sker |
| "gentag 10 gange" | "bliv ved indtil brugeren skriver 0" |
| "gennemløb alle elementer" | "bliv ved indtil gættet er rigtigt" |

Eksempel på noget, der passer til `for`:

```java
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
```

Eksempel på noget, der passer til `while`:

```java
Scanner scanner = new Scanner(System.in);

int number = -1;

while (number != 0) {
    System.out.print("Indtast et tal (0 for at stoppe): ");
    number = scanner.nextInt();
}
```

Her aner vi ikke, hvor mange tal brugeren indtaster.

> **Tommelfingerregel:** Kan du sige "gentag N gange", så brug `for`. Kan du kun sige "bliv ved
> indtil ...", så brug `while`.

---

### Summen af tallene

Et loop bruges tit til at samle et resultat op undervejs:

```java
int sum = 0;

for (int i = 1; i <= 10; i++) {
    sum += i;
}

System.out.println("Summen er " + sum);
```

Output:

```text
Summen er 55
```

Bemærk at `sum` bliver oprettet **før** loopet. Havde vi skrevet `int sum = 0;` inde i loopet,
ville den blive nulstillet ved hvert gennemløb, og resultatet ville blive `10`.

Det samme mønster bruges til at tælle noget:

```java
int count = 0;

for (int i = 1; i <= 100; i++) {

    if (i % 7 == 0) {
        count++;
    }
}

System.out.println("Der er " + count + " tal mellem 1 og 100 der er delelige med 7");
```

---

### `break` – stop loopet nu

`break` afbryder loopet med det samme:

```java
for (int i = 1; i <= 10; i++) {

    if (i == 5) {
        break;
    }

    System.out.println(i);
}

System.out.println("Færdig");
```

Output:

```text
1
2
3
4
Færdig
```

Da `i` bliver `5`, hopper vi helt ud af loopet. `5` bliver aldrig skrevet ud, og resten
(6-10) bliver heller ikke.

### `continue` – spring dette gennemløb over

`continue` springer resten af **dette ene** gennemløb over og går videre til det næste:

```java
for (int i = 1; i <= 10; i++) {

    if (i % 2 != 0) {
        continue;
    }

    System.out.println(i);
}
```

Output:

```text
2
4
6
8
10
```

De ulige tal bliver sprunget over, men loopet fortsætter.

> Vær forsigtig med `continue` i et `while`-loop! Hvis ændringen af tælleren står nederst i
> loopet, bliver den sprunget over – og så har du et uendeligt loop.

Det samme program kan i øvrigt skrives uden `continue`:

```java
for (int i = 1; i <= 10; i++) {

    if (i % 2 == 0) {
        System.out.println(i);
    }
}
```

Ofte er den version lettere at læse. Brug `break` og `continue`, når de gør koden **klarere** – ikke
bare fordi de findes.

---

### Nested loops – et loop inde i et loop

Man kan sagtens sætte et loop inde i et andet:

```java
for (int i = 1; i <= 3; i++) {

    for (int j = 1; j <= 2; j++) {
        System.out.println("i = " + i + ", j = " + j);
    }
}
```

Output:

```text
i = 1, j = 1
i = 1, j = 2
i = 2, j = 1
i = 2, j = 2
i = 3, j = 1
i = 3, j = 2
```

Det **indre** loop kører helt igennem, hver gang det **ydre** loop kører én gang.

Derfor bliver koden inde i det indre loop kørt `3 × 2 = 6` gange i alt.

> **Regnereglen:** Ydre gentagelser **gange** indre gentagelser. Et loop der kører 1000 gange
> inde i et loop der kører 1000 gange, giver en million gennemløb. Det er værd at have i baghovedet.

### En trekant af stjerner

Nested loops bruges ofte til at tegne noget i to dimensioner:

```java
for (int row = 1; row <= 5; row++) {

    for (int star = 1; star <= row; star++) {
        System.out.print("*");
    }

    System.out.println();
}
```

Output:

```text
*
**
***
****
*****
```

Læg mærke til to ting:

* Det indre loop bruger `System.out.print` **uden** `ln` – så alt kommer på samme linje.
* `System.out.println()` uden noget imellem parenteserne laver et linjeskift. Den står i det
  **ydre** loop, så vi skifter linje én gang pr. række.
* Det indre loop tæller til `row` – altså til en værdi, der ændrer sig. Det er tilladt!

### Gangetabellen

```java
for (int i = 1; i <= 3; i++) {

    for (int j = 1; j <= 3; j++) {
        System.out.print(i * j + "\t");
    }

    System.out.println();
}
```

Output:

```text
1	2	3
2	4	6
3	6	9
```

`\t` er et tabulatortegn – det gør kolonnerne pæne.

---

### Uendelige loops

Ligesom med `while` kan et `for`-loop køre for evigt, hvis betingelsen aldrig bliver falsk:

```java
for (int i = 1; i <= 10; i--) {      // ← tæller den forkerte vej
    System.out.println(i);
}
```

Her bliver `i` mindre og mindre, så `i <= 10` er altid sandt.

Kører du et uendeligt loop ved et uheld, kan du stoppe programmet med den røde firkant ⏹ i
IntelliJ.

Man kan også skrive et bevidst uendeligt loop:

```java
while (true) {
    // kører indtil noget kalder break
}
```

Det giver mening, når man har en `break` inde i loopet – men skriv aldrig `while (true)` uden at
vide præcis, hvad der får loopet til at stoppe.

---

### Kan du forudsige resultatet?

Svar **uden** at køre koden. Skriv dine svar ned, og tjek dem bagefter.

#### Eksempel 1

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

Hvor mange linjer bliver skrevet ud? Hvad er det første og det sidste tal?

#### Eksempel 2

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

Hvad er forskellen fra eksempel 1?

#### Eksempel 3

```java
for (int i = 10; i > 0; i -= 3) {
    System.out.println(i);
}
```

#### Eksempel 4

```java
int sum = 0;

for (int i = 1; i <= 4; i++) {
    sum += i;
}

System.out.println(sum);
```

#### Eksempel 5

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        System.out.print("x");
    }
}
```

Hvor mange `x` bliver skrevet ud?

#### Eksempel 6

```java
for (int i = 1; i <= 5; i++) {

    if (i == 3) {
        continue;
    }

    System.out.println(i);
}
```

#### Eksempel 7

```java
for (int i = 1; i <= 5; i++) {

    if (i == 3) {
        break;
    }

    System.out.println(i);
}
```

#### Eksempel 8

```java
for (int i = 0; i < 3; i++);
{
    System.out.println("Hej");
}
```

> Se godt efter. Hvor mange gange bliver `Hej` skrevet ud – og hvorfor?

---

## Det vigtigste at tage med

Efter denne forberedelse skal du især kunne:

* skrive grundformen `for (start; betingelse; ændring) { ... }`
* forklare at de tre dele adskilles med **semikolon**
* forklare rækkefølgen: start én gang → betingelse → kode → ændring → betingelse → ...
* forklare at et loop kan køre **nul** gange
* tælle op, ned og i spring
* vælge mellem `for` og `while` ud fra, om du kender antallet af gentagelser
* opsamle et resultat i en variabel, der er oprettet **før** loopet
* bruge `break` og `continue`, og forklare forskellen
* skrive et nested loop og regne ud, hvor mange gennemløb det giver i alt
* genkende et uendeligt loop

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md)
