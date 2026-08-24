# Opgaver – I/O: Scanner og print

I disse opgaver skal du arbejde med `System.out.print`, `System.out.println` og `Scanner`.

## Kom i gang

Opret et nyt Java-projekt i IntelliJ, eller brug det projekt, du allerede har til undervisningen.

Husk at importere `Scanner` øverst i filen:

```java
import java.util.Scanner;
```

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

---

## Opgave 1 – Sig hej til brugeren

Opret en `Scanner`, og bed brugeren om at skrive sit navn med `nextLine()`.

Udskriv derefter:

```text
Hej [navn]!
```

Eksempel: hvis brugeren skriver `Sofie`, skal programmet skrive:

```text
Hej Sofie!
```

---

## Opgave 2 – Print uden linjeskift

Brug **udelukkende** `System.out.print()` (ikke `println`) til at udskrive tre ord, så de ender på
**samme linje**:

```text
Java er sjovt
```

Prøv derefter at ændre det **sidste** kald til `System.out.println()`, og se, hvad der sker.

Hvad er forskellen?

---

## Opgave 3 – Din alder

Opret en `Scanner`, og bed brugeren om at skrive sin alder med `nextInt()`.

Udskriv:

```text
Du er [alder] år gammel.
```

Eksempel: hvis brugeren skriver `21`, skal programmet skrive:

```text
Du er 21 år gammel.
```

---

## Opgave 4 – Navn og alder

Opret en `Scanner`, og læs **både** navn (med `nextLine()`) og alder (med `nextInt()`).

Udskriv begge oplysninger i én sætning:

```text
Hej [navn], du er [alder] år gammel.
```

Eksempel:

```text
Hej Sofie, du er 21 år gammel.
```

> **Tip:** Husk at læse navnet **inden** du læser alderen.

---

## Opgave 5 – Tal med decimal

Opret en `Scanner`, og bed brugeren om at indtaste en pris i kroner som decimaltal med
`nextDouble()`.

Udskriv prisen med teksten:

```text
Prisen er [pris] kr.
```

Eksempel: hvis brugeren skriver `49.95`, skal programmet skrive:

```text
Prisen er 49.95 kr.
```

---

## Opgave 6 – Simpel regnemaskine – addition

Opret en `Scanner`, og bed brugeren om at indtaste to heltal – ét ad gangen.

Udregn summen, og udskriv:

```text
[tal1] + [tal2] = [sum]
```

Eksempel:

```text
5 + 3 = 8
```

---

## Opgave 7 – BMI-beregner

Opret en `Scanner`, og bed brugeren om:

1. højde i meter (brug `nextDouble()`)
2. vægt i kg (brug `nextDouble()`)

Beregn BMI med formlen:

```text
BMI = vægt / (højde * højde)
```

Udskriv:

```text
Dit BMI er: [bmi]
```

Eksempel: højde `1.75` og vægt `70.0` giver:

```text
Dit BMI er: 22.857142857142858
```

> **Bemærk:** Vi bruger ikke `if`-sætninger endnu – udregn og udskriv blot resultatet.

---

## Opgave 8 – Formel hilsen

Opret en `Scanner`, og læs fornavn og efternavn som **to separate** `nextLine()`-kald.

Udskriv derefter:

```text
Kære [efternavn], [fornavn]
Velkommen til Java!
```

Eksempel: hvis brugeren skriver `Sofie` og `Hansen`, skal programmet skrive:

```text
Kære Hansen, Sofie
Velkommen til Java!
```

---

## Opgave 9 – Omregning af valuta

Opret en `Scanner`, og bed brugeren om et beløb i danske kroner med `nextDouble()`.

Omregn beløbet til euro med en fast kurs:

```text
1 EUR = 7.46 DKK
```

Udskriv:

```text
[kroner] DKK svarer til [euro] EUR.
```

Eksempel: hvis brugeren skriver `100.0`, skal programmet skrive:

```text
100.0 DKK svarer til 13.40 EUR.
```

Brug `String.format("%.2f", ...)` til at formatere eurobeløbet til præcis 2 decimaler.

---

## Opgave 10 – Mini-profil

Opret en `Scanner`, og læs tre oplysninger fra brugeren:

1. navn (med `nextLine()`)
2. alder (med `nextInt()`)
3. favoritfarve (med `next()`)

Udskriv derefter en formateret profil:

```text
=== Min profil ===
Navn:         [navn]
Alder:        [alder]
Favoritfarve: [farve]
==================
```

Eksempel:

```text
=== Min profil ===
Navn:         Sofie
Alder:        21
Favoritfarve: blå
==================
```

> **Tip:** Brug en kombination af `System.out.println()` og `System.out.print()` til at styre
> linjeskiftene. Pas på rækkefølgen af dine kald til `Scanner`, når du blander `nextLine()`,
> `nextInt()` og `next()`.

---

## Udfordring – Temperaturomregner

Opret en `Scanner`, og bed brugeren om en temperatur i **Celsius** (brug `nextDouble()`).

Omregn til **Fahrenheit** med formlen:

```text
F = C * 9 / 5 + 32
```

og til **Kelvin** med formlen:

```text
K = C + 273.15
```

Udskriv alle tre temperaturer:

```text
[C] °C = [F] °F = [K] K
```

Eksempel: hvis brugeren skriver `100.0`, skal programmet skrive:

```text
100.0 °C = 212.0 °F = 373.15 K
```

---

## Ekstra udfordring – Temperaturomregner (fra Fahrenheit)

Opret en `Scanner`, og bed brugeren om en temperatur i **Fahrenheit** (brug `nextDouble()`).

Omregn til **Celsius** og **Kelvin**.

Udskriv alle tre temperaturer:

```text
[F] °F = [C] °C = [K] K
```

Eksempel: hvis brugeren skriver `212.0`, skal programmet skrive:

```text
212.0 °F = 100.0 °C = 373.15 K
```

<details>
<summary>Hint: Vis formel for Celsius</summary>

```text
C = (F - 32) * 5 / 9
```

</details>

<details>
<summary>Hint: Vis formel for Kelvin</summary>

Brug først `C` fra hintet for Celsius.

```text
K = C + 273.15
```

</details>

---

## Opgave 11 – Positiv, negativ eller nul

Bed brugeren om at indtaste et heltal.

Tjek om tallet er:
- positivt
- negativt
- nul

Udskriv en passende besked.

Eksempel:

```text
Tallet er positivt.
```

---

## Opgave 12 – Største af to tal

Bed brugeren om at indtaste to tal.

Udskriv hvilket tal der er størst:

```text
Det største tal er [tal].
```

Hvis de er ens, skal du skrive:

```text
Tallene er ens.
```

---

## Opgave 13 – Lige eller ulige

Bed brugeren om at indtaste et heltal.

Udskriv:

```text
Tallet er lige.
```

eller

```text
Tallet er ulige.
```

> **Hint:** Brug resten ved division med 2.

---

## Opgave 14 – Enkel karakterberegning

Bed brugeren om at indtaste en pointscore mellem 0 og 100.

Omsæt scoren til en karakter med følgende skala:

- 90 eller mere: `12`
- 80–89: `10`
- 70–79: `7`
- 60–69: `4`
- 50–59: `02`
- under 50: `00`

Udskriv karakteren.

---

## Opgave 15 – Ung, voksen eller senior

Bed brugeren om at indtaste sin alder.

Udskriv:
- `Du er et barn.` hvis alderen er under 13
- `Du er teenager.` hvis alderen er mellem 13 og 19
- `Du er voksen.` hvis alderen er mellem 20 og 64
- `Du er senior.` hvis alderen er 65 eller derover

---

## Opgave 16 – Rabat på billet

Bed brugeren om at indtaste:
1. alder
2. normalpris på en billet

Regler:
- børn under 12 år får 50% rabat
- unge mellem 12 og 17 år får 25% rabat
- voksne får ingen rabat

Udskriv den endelige pris.

Eksempel:

```text
Prisen efter rabat er 75.0 kr.
```

---

## Opgave 17 – Tjek adgang

Bed brugeren om at indtaste:
1. alder
2. om de har id-kort (`ja` eller `nej`)

Adgang gives kun hvis brugeren er 18 år eller derover **og** har id-kort.

Udskriv enten:

```text
Adgang godkendt.
```

eller

```text
Adgang afvist.
```

---

## Opgave 18 – Temperatur og beklædning

Bed brugeren om at indtaste temperaturen i grader Celsius.

Udskriv en anbefaling:

- under 0: `Det er meget koldt. Tag vinterjakke på.`
- 0 til 10: `Det er koldt. Tag en varm jakke på.`
- 11 til 20: `Det er mildt. En let jakke er fin.`
- over 20: `Det er varmt. Du behøver ikke en jakke.`

---

## Opgave 19 – Simpel login-kontrol

Opret to faste variabler i koden:

- et brugernavn
- en adgangskode

Bed brugeren om at indtaste et brugernavn og en adgangskode.

Hvis begge passer, så skriv:

```text
Login godkendt.
```

Ellers:

```text
Forkert brugernavn eller adgangskode.
```

---

## Opgave 20 – Minikalkulator

Bed brugeren om at indtaste:
1. første tal
2. en operator som tekst (`+`, `-`, `*` eller `/`)
3. andet tal

Udskriv resultatet af regnestykket.

Eksempel:

```text
8 + 2 = 10
```

Hvis der tastes en ukendt operator, skal du skrive:

```text
Ugyldig operator.
```

---

## Opgave 21 – Minikalkulator med mere robust input

Brug din løsning fra **opgave 20** som udgangspunkt, og lav en ny version af minikalkulatoren, hvor du tænker over, hvilke datatyper der er bedst at bruge til input.

Overvej især:

- Skal tallene være `int`, `double` eller noget tredje?
- Hvad sker der, hvis brugeren skriver et decimaltal?
- Hvad sker der, hvis brugeren skriver noget, der ikke er et tal?
- Hvad sker der, hvis der tastes division med 0?

Udskriv regnestykket, hvis input er gyldigt:

```text
8 + 2 = 10
```

Hvis operatoren er ukendt, skal du skrive:

```text
Ugyldig operator.
```

Hvis input ikke kan bruges, skal du tænke over, hvordan programmet kan reagere på en fornuftig måde.

> **Hint:** Sammenlign denne version med opgave 20, og undersøg, hvad der ændrer sig, når du bruger forskellige datatyper.

---

## Ekstra udfordring – Input via kommandolinjeargumenter

Nogle programmer tager ikke input via `Scanner`, men får i stedet deres input som **kommandolinjeargumenter**. Læs mere om det i [`cmdl.md`](cmdl.md).

Overvej, hvilke af opgaverne i dette ark der **kunne give mening** at løse på den måde.

Svar også på disse spørgsmål:

- Hvilke fordele kan der være ved at bruge kommandolinjeargumenter i stedet for `Scanner`?
- Hvilke udfordringer kan der være ved at tage input på den måde?
- Bliver det tydeligt for brugeren, hvad programmet gør, når input gives som argumenter?
- Hvornår er `Scanner` en bedre løsning end kommandolinjeargumenter?

Skriv derefter en **ny udgave af koden** for en af opgaverne, hvor det giver mening at bruge kommandolinjeargumenter i stedet for `Scanner`.

> **Hint:** Tænk over, hvilke programmer der skal have input **med det samme**, og hvilke der først skal spørge brugeren undervejs.
> **Hint:** Giv programmet et navn, der tydeligt viser, hvad det gør, fx `ArgCalculator`, `CmdLineConverter` eller lignende.

---

## Ekstra udfordring – Gæt et tal uden løkker

Lav et lille program, der kan gætte et tal mellem **1 og 4**, som brugeren tænker på.

Programmet må stille spørgsmål som fx:

- Er tallet større end 2?
- Er tallet større end 3?

Ud fra svarene skal programmet kunne finde det tal, brugeren har tænkt på.

> **Bemærk:** Du må **ikke** bruge løkker til denne opgave. Det emne kommer først næste uge.

Når du har fået programmet til at virke for intervallet **1–4**, så prøv at udvide det, så det også kan gætte tal mellem **1 og 8**.

> **Hint:** Tænk i ja/nej-spørgsmål og if/else-strukturer.

---

## Ekstra udfordring – Små skilte med ASCII-grafik

Lav et lille program, der kan printe et “skilt” i konsollen ved hjælp af **ASCII-grafik**.

Lad brugeren skrive den tekst, der skal stå i skiltet, som input, og lav derefter en boks omkring teksten.

Eksempel:

```text
+------------------+
|   Hej med dig!   |
+------------------+
```

Prøv at lave flere varianter, hvor teksten kan være forskellig, og hvor boksen stadig passer til teksten.

Overvej også, hvordan du kan lave:

- en overskrift i en ramme
- en advarselsboks
- et navneskilt
- en lille menu med ramme omkring

> **Hint:** Tegn som disse kan være nyttige:
> - `+`
> - `-`
> - `|`
> - `/`
> - `\`
> - `*`
> - `#`

> **Hint:** Tænk over, hvordan du kan kombinere tekst, mellemrum og gentagne tegn, så udskriften bliver pæn og tydelig.
```