# Input via kommandolinjeargumenter

Ud over at bruge `Scanner` til at læse input fra brugeren, kan et Java-program også modtage input
**når det startes** – direkte fra kommandolinjen. Det kaldes **kommandolinjeargumenter** (på engelsk:
*command-line arguments*).

Dette er en anderledes måde at give input til programmet på: i stedet for at programmet stopper og
venter, mens det kører, angiver brugeren alle værdier på forhånd, da programmet startes.

---

## Hvad er `args`?

Du har måske lagt mærke til, at `main`-metoden altid ser sådan ud:

```java
public static void main(String[] args) {
```

Parameteren `args` er et **array af Strings** – altså en liste af tekster. Det er her Java gemmer
de argumenter, som brugeren skriver, da programmet startes.

Hvert ord (adskilt af mellemrum) bliver til ét element i arrayet:

| Argument nr. | Indeks i `args` |
|---|---|
| 1. argument | `args[0]` |
| 2. argument | `args[1]` |
| 3. argument | `args[2]` |
| ... | ... |

---

## Et simpelt eksempel

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hej " + args[0]);
    }
}
```

Hvis programmet startes med argumentet `Sofie`, skriver det:

```text
Hej Sofie
```

---

## Sådan gør du i terminalen

Når du har kompileret dit Java-program, kører du det normalt med:

```bash
java Main
```

For at sende argumenter med tilføjer du dem bare efter klassenavnet, adskilt af mellemrum:

```bash
java Main Sofie
```

Flere argumenter:

```bash
java Main Sofie 21 blå
```

Her vil `args[0]` være `"Sofie"`, `args[1]` være `"21"` og `args[2]` være `"blå"`.

Eksempel med tre argumenter:

```java
public class Main {

    public static void main(String[] args) {
        String name = args[0];
        int age = Integer.parseInt(args[1]);
        String color = args[2];

        System.out.println("Navn: " + name);
        System.out.println("Alder: " + age);
        System.out.println("Yndlingsfarve: " + color);
    }
}
```

Kør det med:

```bash
java Main Sofie 21 blå
```

Output:

```text
Navn: Sofie
Alder: 21
Yndlingsfarve: blå
```

> **Bemærk:** Argumenter er altid af typen `String`. Vil du bruge et tal, skal du konvertere det –
> f.eks. med `Integer.parseInt(args[1])` for heltal eller `Double.parseDouble(args[1])` for
> decimaltal.

---

## Argumenter med mellemrum

Hvis ét argument selv indeholder mellemrum, sætter du det i anførselstegn:

```bash
java Main "Sofie Hansen" 21 blå
```

Nu er `args[0]` hele teksten `"Sofie Hansen"`.

---

## Sådan gør du i IntelliJ

I IntelliJ behøver du ikke terminalen for at sende kommandolinjeargumenter. Du kan i stedet
konfigurere dem i selve IntelliJ.

### Trin 1 – Åbn Run/Debug Configurations

Klik på rullemenuen øverst til højre (ved siden af den grønne play-knap) og vælg
**Edit Configurations...**.

![Edit Configurations](https://i.imgur.com/placeholder.png)

### Trin 2 – Find feltet Program arguments

I vinduet der åbner, finder du feltet **Program arguments** (under fanen *Run* eller direkte synligt,
afhængigt af din IntelliJ-version).

### Trin 3 – Skriv dine argumenter

Skriv dine argumenter i feltet, adskilt af mellemrum – præcis som du ville gøre i terminalen:

```
Sofie 21 blå
```

### Trin 4 – Kør programmet

Klik **OK** og kør programmet som normalt med den grønne play-knap. IntelliJ sender nu argumenterne
til `args`-arrayet.

> **Tip:** Du kan have flere konfigurationer med forskellige argumenter, så du nemt kan teste
> programmet med forskelligt input.

---

## Hvad sker der, hvis der ikke er argumenter?

Hvis programmet forventer argumenter, men ingen gives, vil det kaste en fejl
(`ArrayIndexOutOfBoundsException`), når du forsøger at tilgå f.eks. `args[0]`.

Du kan beskytte mod det ved at tjekke, om der er nok argumenter:

```java
public class Main {

    public static void main(String[] args) {
        if (args.length < 1) {
            System.out.println("Fejl: Angiv venligst et navn som argument.");
            return;
        }

        System.out.println("Hej " + args[0]);
    }
}
```

`args.length` fortæller, hvor mange argumenter der er givet.

---

## Vigtige ting at huske

* `args` er et `String`-array med de argumenter, brugeren angiver ved opstart
* I terminalen skrives argumenterne efter klassenavnet: `java Main arg1 arg2`
* I IntelliJ angives argumenterne under **Edit Configurations → Program arguments**
* Argumenter er altid tekst – brug `Integer.parseInt()` eller `Double.parseDouble()` til tal
* Brug `args.length` til at tjekke, om der er givet nok argumenter
