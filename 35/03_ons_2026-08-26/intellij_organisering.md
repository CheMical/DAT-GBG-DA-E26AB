# Organisering af Java-projekter og packages i IntelliJ

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

# Samlet oversigt over projekter og packages

```text
uge35-intro-java/
    src/
        dag1_introdag_studiegrupper/
            Main.java

        dag2_installation_java_notepad/
            Main.java

        dag3_variable_datatyper_aritmetik/
            Main.java

        dag4_logiske_operatorer_betingelser/
            Main.java

        dag5_io_scanner_print_git/
            Main.java


uge36-loops-arrays-strings/
    src/
        dag1_while_loops/
            Main.java

        dag2_for_loops_while_loops/
            Main.java

        dag3_arrays/
            Main.java

        dag4_itf/
            Main.java

        dag5_loops_strings_repetition/
            Main.java


uge37-klasser-objekter-metoder/
    src/
        dag1_objekter_klasser_intro/
            Main.java
            Book.java

        dag2_objekter_klasser_indkapsling/
            Main.java
            Book.java

        dag3_enum_switch/
            Main.java

        dag4_metoder/
            Main.java

        dag5_metoder/
            Main.java

        bogsamling/
            Main.java
            Book.java


uge38-relationer-arraylist/
    src/
        dag1_aktivitetsdiagram_debugger/
            Main.java

        dag2_objekter_i_objekter_klassediagrammer/
            Main.java
            Book.java
            Library.java

        dag3_arraylist/
            Main.java

        dag4_itf/
            Main.java

        dag5_arraylist_soegning_redigering/
            Main.java

        bogsamling/
            Main.java
            Book.java
            Library.java
```

---

# Sådan opretter du et Java-projekt i IntelliJ

## Trin 1: Opret et nyt projekt

Når du starter på en ny uge, skal du oprette et nyt IntelliJ-projekt.

Eksempel på projektnavne:

```text
uge35-intro-java
uge36-loops-arrays-strings
uge37-klasser-objekter-metoder
uge38-relationer-arraylist
```

Gør sådan:

1. Åbn IntelliJ
2. Vælg **New Project**
3. Vælg **Java**
4. Giv projektet et navn, fx:

```text
uge37-klasser-objekter-metoder
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
uge37-klasser-objekter-metoder/
    src/
```

---

# Sådan opretter du en package

## Trin 3: Opret en ny package

En package bruges til at organisere dine Java-klasser.

Vi laver typisk én package pr. undervisningsgang.

Eksempel på package-navne:

```text
dag1_objekter_klasser_intro
dag2_objekter_klasser_indkapsling
dag3_enum_switch
bogsamling
```

Gør sådan:

1. Højreklik på `src`
2. Vælg **New**
3. Vælg **Package**
4. Skriv navnet på pakken, fx:

```text
dag1_objekter_klasser_intro
```

5. Tryk **Enter**

Nu har du oprettet en package.

---

# Sådan opretter du en Main-klasse i en package

## Trin 4: Opret klassen `Main`

Når du har oprettet en package, skal du oprette en `Main`-klasse i den.

Gør sådan:

1. Højreklik på pakken, fx `dag1_objekter_klasser_intro`
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
package dag1_objekter_klasser_intro;

public class Main {
}
```

Bemærk den første linje:

```java
package dag1_objekter_klasser_intro;
```

Den fortæller, at klassen ligger i pakken `dag1_objekter_klasser_intro`.

---

# Sådan opretter du main-metoden

## Trin 5: Tilføj `main`-metoden

Inde i `Main`-klassen skal du skrive en `main`-metode:

```java
package dag1_objekter_klasser_intro;

public class Main {

    public static void main(String[] args) {
        System.out.println("Hej fra dag 1");
    }
}
```

Du kan køre programmet ved at trykke på den grønne pil ud for `main`-metoden.

---

# Sådan opretter du andre klasser

Ud over `Main` skal du ofte oprette andre klasser, fx `Book`, `Library`, `Person` eller `Account`.

Gør sådan:

1. Højreklik på den package, hvor klassen skal ligge
2. Vælg **New**
3. Vælg **Java Class**
4. Skriv klassens navn, fx:

```text
Book
```

5. Tryk **Enter**

Eksempel:

```java
package bogsamling;

public class Book {

}
```

---

# Eksempel: Flere Main-klasser i samme projekt

I samme IntelliJ-projekt kan du have denne struktur:

```text
src/
    dag1_objekter_klasser_intro/
        Main.java

    dag2_objekter_klasser_indkapsling/
        Main.java

    bogsamling/
        Main.java
```

Det er tilladt, fordi de tre `Main`-klasser ligger i hver sin package.

De fulde navne er:

```text
dag1_objekter_klasser_intro.Main
dag2_objekter_klasser_indkapsling.Main
bogsamling.Main
```

---

# Regler for navngivning

## Projektnavne

Projektnavne må gerne være beskrivende.

Eksempler:

```text
uge35-intro-java
uge36-loops-arrays-strings
uge37-klasser-objekter-metoder
uge38-relationer-arraylist
```

Det er fint at bruge bindestreg i projektnavne.

---

## Package-navne

Package-navne bør være korte og uden mellemrum.

Eksempler:

```text
dag1_introdag_studiegrupper
dag2_variable_datatyper
dag3_enum_switch
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

eller endnu bedre et mere præcist navn:

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

---

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
    dag1_objekter_klasser_intro/
        Main.java

    dag2_objekter_klasser_indkapsling/
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

# Samlet progression

Den samlede progression i projekterne kan ses sådan:

```text
uge35-intro-java
    ↓
IntelliJ, Main, output, variable, datatyper og simple beregninger

uge36-loops-arrays-strings
    ↓
while-loops, for-loops, arrays, strings og repetition

uge37-klasser-objekter-metoder
    ↓
Book som simpel klasse, objekter, metoder, enum og switch

uge38-relationer-arraylist
    ↓
Library med mange Book-objekter, ArrayList og 1:mange-relation
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
