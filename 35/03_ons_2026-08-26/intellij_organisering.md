# Organisering af Java-projekter i IntelliJ

## Overordnet idé

I de første uger kommer vi til at arbejde med mange små Java-programmer. Mange af dem skal bruges til at afprøve et bestemt begreb, for eksempel variable, betingelser, løkker, klasser eller objekter.

Derfor organiserer vi koden sådan:

* Vi laver **ét IntelliJ-projekt pr. uge**
* Inde i projektet laver vi **én package pr. undervisningsgang**
* Hver package kan have sin egen `Main`-klasse
* Det gennemgående projekt får sin egen package, når det giver mening

På den måde kan vi gemme koden fra hver undervisningsgang uden at overskrive tidligere eksempler.

---

## Hvorfor bruger vi packages?

I Java kan man ikke have to klasser med samme navn i samme package.

Hvis vi for eksempel har én klasse, der hedder `Main`, kan vi ikke bare oprette en ny klasse med navnet `Main` samme sted.

Men vi må gerne have flere `Main`-klasser, hvis de ligger i forskellige packages.

Eksempel:

```text
dag1_klasser.Main
dag2_objekter_metoder.Main
bogsamling.Main
```

Her hedder klasserne alle sammen `Main`, men de ligger i hver sin package.

Man kan tænke på en package som en mappe, der hjælper os med at organisere vores Java-klasser.

---

# Projekter i de første uger

## Uge 35: Introduktion til Java og IntelliJ

**Forslag til projektnavn:**

```text
uge35-intro-java
```

Uge 35 bruges til den første introduktion til Java og IntelliJ.

Mulig struktur:

```text
uge35-intro-java/
    src/
        dag1_intro_intellij/
            Main.java

        dag2_variable_datatyper/
            Main.java

        dag3_beregninger/
            Main.java
```

Eksempel på `Main` i uge 35:

```java
package dag1_intro_intellij;

public class Main {

    public static void main(String[] args) {
        System.out.println("Mit første Java-program");
    }
}
```

---

## Uge 36: Betingelser, input og løkker

**Forslag til projektnavn:**

```text
uge36-betingelser-loops
```

Uge 36 bruges til grundlæggende kontrolstrukturer.

Mulig struktur:

```text
uge36-betingelser-loops/
    src/
        dag1_betingelser/
            Main.java

        dag2_input_og_validering/
            Main.java

        dag3_loops/
            Main.java
```

Eksempel på `Main` i uge 36:

```java
package dag1_betingelser;

public class Main {

    public static void main(String[] args) {
        int age = 18;

        if (age >= 18) {
            System.out.println("Du er myndig");
        } else {
            System.out.println("Du er ikke myndig");
        }
    }
}
```

---

## Uge 37: Klasser og objekter

**Forslag til projektnavn:**

```text
uge37-klasser-og-objekter
```

Uge 37 bruges til introduktion til objektorienteret programmering.

Mulig struktur:

```text
uge37-klasser-og-objekter/
    src/
        dag1_klasser/
            Main.java
            Book.java

        dag2_objekter_metoder/
            Main.java
            Book.java

        dag3_indkapsling/
            Main.java
            Book.java

        bogsamling/
            Main.java
            Book.java
```

Package `bogsamling` bruges til det gennemgående projekt **Min bogsamling**.

I uge 37 starter projektet simpelt med én klasse:

```text
bogsamling/
    Main.java
    Book.java
```

---

## Uge 38: Relationer og ArrayList

**Forslag til projektnavn:**

```text
uge38-relationer-og-arraylist
```

Uge 38 bruges til at arbejde med flere objekter og relationer mellem objekter.

Mulig struktur:

```text
uge38-relationer-og-arraylist/
    src/
        dag1_arraylist/
            Main.java

        dag2_relationer/
            Main.java
            Book.java
            Library.java

        dag3_bogsamling_udvidelse/
            Main.java

        bogsamling/
            Main.java
            Book.java
            Library.java
```

I uge 38 udvides projektet **Min bogsamling** med klassen `Library`.

```text
bogsamling/
    Main.java
    Book.java
    Library.java
```

Relationen er:

```text
Et Library har mange Book-objekter
```

---


## Trin 1: Opret et nyt Java-projekt

Når du starter på en ny uge, skal du oprette et nyt IntelliJ-projekt.

Eksempel på projektnavne:

```text
uge35-intro-java
uge36-betingelser-loops
uge37-klasser-og-objekter
uge38-relationer-og-arraylist
```

### Trin i IntelliJ

1. Åbn IntelliJ
2. Vælg **New Project**
3. Vælg **Java**
4. Giv projektet et navn, fx:

```text
uge37-klasser-og-objekter
```

5. Vælg hvor projektet skal gemmes
6. Klik **Create**

---


## Trin 2: Find `src`-mappen

Når projektet er oprettet, skal du finde mappen:

```text
src
```

Det er i `src`, at Java-koden skal ligge.

Eksempel:

```text
uge37-klasser-og-objekter/
    src/
```

---

## Trin 3: Opret en package

En package bruges til at organisere dine klasser.

Vi laver typisk én package pr. undervisningsgang.

Eksempel:

```text
dag1_klasser
dag2_objekter_metoder
dag3_indkapsling
bogsamling
```

### Trin i IntelliJ

1. Højreklik på `src`
2. Vælg **New**
3. Vælg **Package**
4. Skriv navnet på pakken, fx:

```text
dag1_klasser
```

5. Tryk **Enter**

Nu har du oprettet en package.

---

## Trin 4: Opret klassen Main

Når du har oprettet en package, skal du oprette en `Main`-klasse i den.

### Trin i IntelliJ

1. Højreklik på pakken, fx `dag1_klasser`
2. Vælg **New**
3. Vælg **Java Class**
4. Skriv:

```text
Main
```

5. Tryk **Enter**

IntelliJ opretter nu filen `Main.java`.

Den vil typisk se sådan ud:

```java
package dag1_klasser;

public class Main {
}
```

Bemærk den første linje:

```java
package dag1_klasser;
```

Den fortæller, at klassen ligger i pakken `dag1_klasser`.

---


## Trin 5: Tilføj main-metoden

Inde i `Main`-klassen skal du skrive en `main`-metode:

```java
package dag1_klasser;

public class Main {

    public static void main(String[] args) {
        System.out.println("Hej fra dag 1");
    }
}
```

Du kan køre programmet ved at trykke på den grønne pil ud for `main`-metoden.

---

# Eksempel: Flere Main-klasser i samme projekt

I samme IntelliJ-projekt kan du have denne struktur:

```text
src/
    dag1_klasser/
        Main.java

    dag2_objekter_metoder/
        Main.java

    bogsamling/
        Main.java
```

Det er tilladt, fordi de tre `Main`-klasser ligger i hver sin package.

De fulde navne er:

```text
dag1_klasser.Main
dag2_objekter_metoder.Main
bogsamling.Main
```

---

# Det gennemgående projekt: Min bogsamling

Ud over de små eksempler laver vi et gennemgående projekt, som hedder:

```text
Min bogsamling
```

Projektet placeres i en package med navnet:

```text
bogsamling
```

I starten indeholder projektet kun en `Book`-klasse:

```text
src/
    bogsamling/
        Main.java
        Book.java
```

Senere udvider vi projektet med en `Library`-klasse:

```text
src/
    bogsamling/
        Main.java
        Book.java
        Library.java
```

På den måde kan vi arbejde videre med det samme lille projekt, efterhånden som vi lærer nye begreber.

---

# Forslag til navne på packages

## Uge 35

```text
dag1_intro_intellij
dag2_variable_datatyper
dag3_beregninger
```

## Uge 36

```text
dag1_betingelser
dag2_input_og_validering
dag3_loops
```

## Uge 37

```text
dag1_klasser
dag2_objekter_metoder
dag3_indkapsling
bogsamling
```

## Uge 38

```text
dag1_arraylist
dag2_relationer
dag3_bogsamling_udvidelse
bogsamling
```

---

# Regler for navngivning

## Projektnavne

Projektnavne må gerne være beskrivende.

Eksempel:

```text
uge37-klasser-og-objekter
```

Det er fint at bruge bindestreg i projektnavne.

## Package-navne

Package-navne bør være korte og uden mellemrum.

Eksempel:

```text
dag1_klasser
dag2_objekter_metoder
bogsamling
```

Brug små bogstaver.

Undgå æ, ø og å i package-navne.

Brug derfor ikke:

```text
dag1_øvelse
```

Brug i stedet:

```text
dag1_oevelse
```

eller endnu bedre:

```text
dag1_klasser
```

Undgå også mellemrum.

Brug ikke:

```text
Dag 1 Klasser
```

Brug i stedet:

```text
dag1_klasser
```

## Klassenavne

Klassenavne skrives med stort begyndelsesbogstav.

Eksempler:

```text
Main
Book
Library
Person
Account
```

---

# Hvad skal du gøre hver undervisningsgang?

Når vi starter en ny undervisningsgang:

1. Åbn ugens IntelliJ-projekt
2. Opret en ny package til dagens kode
3. Opret en ny `Main`-klasse i pakken
4. Afprøv dagens eksempler i `main`-metoden
5. Gem koden, så du kan finde den igen senere

Eksempel:

```text
src/
    dag1_klasser/
        Main.java

    dag2_objekter_metoder/
        Main.java
```

---

# Hvad skal du gøre, når du arbejder med projektet?

Når du arbejder med det gennemgående projekt **Min bogsamling**, skal du bruge pakken:

```text
bogsamling
```

Her skal dine projektklasser ligge:

```text
src/
    bogsamling/
        Main.java
        Book.java
        Library.java
```

Du skal altså ikke lave en ny `Book`-klasse hver gang i en ny dag-package, hvis du arbejder videre på projektet.

---

# Eksempel på færdig struktur for uge 35

```text
uge35-intro-java/
    src/
        dag1_intro_intellij/
            Main.java

        dag2_variable_datatyper/
            Main.java

        dag3_beregninger/
            Main.java
```

---

# Eksempel på færdig struktur for uge 36

```text
uge36-betingelser-loops/
    src/
        dag1_betingelser/
            Main.java

        dag2_input_og_validering/
            Main.java

        dag3_loops/
            Main.java
```

---

# Eksempel på færdig struktur for uge 37

```text
uge37-klasser-og-objekter/
    src/
        dag1_klasser/
            Main.java
            Book.java

        dag2_objekter_metoder/
            Main.java
            Person.java
            Account.java

        dag3_indkapsling/
            Main.java

        bogsamling/
            Main.java
            Book.java
```

---

# Eksempel på færdig struktur for uge 38

```text
uge38-relationer-og-arraylist/
    src/
        dag1_arraylist/
            Main.java

        dag2_relationer/
            Main.java
            Book.java
            Library.java

        dag3_bogsamling_udvidelse/
            Main.java

        bogsamling/
            Main.java
            Book.java
            Library.java
```

---

# Samlet progression

Den samlede progression i projekterne kan ses sådan:

```text
uge35-intro-java
    ↓
variable, output, simple beregninger

uge36-betingelser-loops
    ↓
input, if/else, while, for

uge37-klasser-og-objekter
    ↓
Book som simpel klasse

uge38-relationer-og-arraylist
    ↓
Library med mange Book-objekter
```

---

# Kort opsummering

Vi bruger denne struktur:

```text
Ét projekt pr. uge
Én package pr. undervisningsgang
Én Main-klasse pr. package
Én separat package til det gennemgående projekt, når det giver mening
```

Det gør det nemmere at holde styr på koden og samtidig gemme tidligere eksempler.

På den måde kan du altid gå tilbage og se, hvad du lavede i tidligere undervisningsgange, uden at din nye kode overskriver den gamle.
