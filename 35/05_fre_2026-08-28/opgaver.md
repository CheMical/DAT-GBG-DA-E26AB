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
