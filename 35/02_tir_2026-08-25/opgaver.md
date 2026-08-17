# Opgaver – Introdag 2: installation og Java i Notepad

Dagens opgaver handler om at få værktøjerne på plads og se, hvad der sker, når et Java-program
bliver til.

> **Arbejd i studiegruppen.** Er du færdig før de andre, så hjælp dem. Målet er, at **alle** i
> gruppen går herfra med en virkende opsætning – ikke at du selv bliver først færdig.

---

## Del 1 – Installation

### Opgave 1 – Installér JDK

Hent og installér **JDK 21** eller nyere fra [adoptium.net](https://adoptium.net/).

Kontrollér bagefter i en terminal:

```bash
java -version
javac -version
```

Begge kommandoer skal svare med et versionsnummer. Eksempel:

```text
openjdk version "21.0.5" 2024-10-15
javac 21.0.5
```

> Får du `command not found` eller `'javac' is not recognized`, er JDK'en enten ikke installeret
> eller ikke lagt i din PATH. Sig til – det er en klassisk forhindring, og den er hurtig at løse.

### Opgave 2 – Installér IntelliJ IDEA

Hent **IntelliJ IDEA Community Edition** fra
[jetbrains.com/idea/download](https://www.jetbrains.com/idea/download/) og installér den.

Start programmet, og se at det åbner uden fejl.

### Opgave 3 – Installér Git

Hent og installér Git fra [git-scm.com/downloads](https://git-scm.com/downloads).

Kontrollér i en terminal:

```bash
git --version
```

Sæt derefter dit navn og din mail, så dine commits kan spores til dig:

```bash
git config --global user.name "Dit Navn"
git config --global user.email "din@mail.dk"
```

Kontrollér:

```bash
git config --global --list
```

> Vi bruger ikke Git i dag – men vi bruger det fra uge 39 og resten af semesteret, og det er
> nemmere at få installeret nu, hvor vi sidder sammen.

---

## Del 2 – Java i Notepad

### Opgave 4 – Dit første program

Opret en mappe til dagens arbejde. Lav en fil i mappen, der hedder præcis:

```text
Main.java
```

Skriv følgende i filen med en almindelig teksteditor:

```java
public class Main {

    public static void main(String[] args) {

        System.out.println("Hello, world!");
    }
}
```

Kompilér og kør:

```bash
javac Main.java
java Main
```

Forventet output:

```text
Hello, world!
```

### Opgave 5 – Kig på det, der blev lavet

Efter `javac Main.java` er der kommet en ny fil i mappen.

1. Hvad hedder den?
2. Åbn den i din teksteditor. Hvad ser du?
3. Hvorfor kan du ikke læse den?
4. Slet `.class`-filen, og prøv at køre `java Main` igen. Hvad sker der?
5. Kør `javac Main.java` igen, og så `java Main`. Virker det nu?

### Opgave 6 – Skriv mere ud

Udvid programmet, så det skriver flere linjer:

```text
Hello, world!
My name is ...
I am studying to become a datamatiker
```

Husk at du skal køre **både** `javac` og `java` igen, hver gang du har ændret i filen. Prøv med
vilje kun at køre `java Main` efter en ændring – hvad sker der?

---

## Del 3 – Fejl er information

For hver af de følgende opgaver skal du:

1. Lave fejlen med vilje
2. Køre `javac Main.java`
3. **Læse fejlmeddelelsen og skrive den ned med dine egne ord**
4. Rette fejlen igen

### Opgave 7 – Manglende semikolon

Fjern semikolonet efter `System.out.println("Hello, world!")`.

* Hvilken linje peger compileren på?
* Hvad betyder `^`-tegnet?

### Opgave 8 – Forkert store og små bogstaver

Skriv `system.out.println(...)` med lille `s`.

* Hvad hedder fejlen?
* Hvorfor kan Java ikke bare regne ud, hvad du mente?

### Opgave 9 – Manglende krøllet parentes

Slet den sidste `}`.

* Hvor mange fejl får du?
* Peger compileren på det rigtige sted?

### Opgave 10 – Filnavn og klassenavn passer ikke

Omdøb klassen inde i filen fra `Main` til `Hello`, men lad filen hedde `Main.java`.

* Hvad siger compileren?
* Ret det på to forskellige måder: først ved at ændre klassenavnet tilbage, derefter ved at omdøbe
  filen i stedet.

### Opgave 11 – Stavefejl i main

Skriv `Main`-metoden med stort M:

```java
public static void Main(String[] args) {
```

* Kan programmet **kompileres**?
* Kan det **køres**?
* Hvad er forskellen på de to slags fejl?

> Denne opgave er vigtig. En fejl, compileren fanger, er den nemme slags. En fejl, der først dukker
> op, når programmet kører, er den svære slags. Du kommer til at møde begge dele hele semesteret.

---

## Del 4 – IntelliJ

### Opgave 12 – Samme program i IntelliJ

Opret et nyt Java-projekt i IntelliJ, lav en klasse `Main`, og få den til at skrive
`Hello, world!` ud.

Brug genvejene:

* `main` + <kbd>Tab</kbd>
* `sout` + <kbd>Tab</kbd>

### Opgave 13 – Find .class-filen igen

IntelliJ kompilerer også til `.class`-filer – den viser dem bare ikke.

Find mappen `out` i dit projekt (i filsystemet, ikke i IntelliJ). Kan du finde `Main.class`?

Det er de samme to skridt som før: IntelliJ kører `javac` og `java` for dig.

### Opgave 14 – Lav fejlene igen

Lav de samme fejl som i opgave 7-10, men nu i IntelliJ.

* Hvornår opdager IntelliJ fejlen – før eller efter du trykker på ▶?
* Hvad markerer den med rødt?
* Prøv at holde musen over den røde markering. Hvad foreslår den?

### Opgave 15 – Prøv genvejene

1. Ødelæg indrykningen i din kode med vilje (fjern mellemrum, ryk linjer ud)
2. Tryk <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>L</kbd> (Mac: <kbd>Cmd</kbd>+<kbd>Alt</kbd>+<kbd>L</kbd>)
3. Hvad skete der?

Prøv også:

* <kbd>Ctrl</kbd>+<kbd>/</kbd> på en linje
* <kbd>Shift</kbd> to gange hurtigt efter hinanden, og søg efter "Reformat Code"

---

## Del 5 – Praktisk

### Opgave 16 – Systemerne

Log på og tjek, at du kan komme ind alle steder:

* [itslearning](https://ek.itslearning.com) – planer og afleveringer
* [Teams](https://teams.microsoft.com/) – al kommunikation. Find din klasses kanal.
* [GitHub-repoet](https://github.com/EK-DAT-GBG-1SEM-E26AB/DAT-GBG-DA-E26AB) – alt
  undervisningsmateriale. Sæt et bogmærke.
* [UMS](https://ums.ek.dk/)
* [TimeEdit](https://cloud.timeedit.net/dk_ek/web) – dit skema
* [Intranet](https://mit.ek.dk/)

### Opgave 17 – GitHub-konto

Har du ikke allerede en GitHub-konto, så opret en nu på
[github.com/signup](https://github.com/signup).

Skriv dit GitHub-brugernavn ned – du får brug for det, når vi starter på projekterne.

---

## Hvis du bliver færdig

1. **Hjælp din studiegruppe.** Det er den vigtigste opgave i dag.
2. Prøv at skrive et program, der bruger variable og regner noget ud – f.eks. omregner en
   temperatur fra celsius til fahrenheit. Vi tager fat i variable i morgen, så du kan roligt kigge
   lidt frem.
3. Prøv at køre dit program fra kommandolinjen **med** et argument:

   ```bash
   java Main hej
   ```

   Kan du få programmet til at skrive `hej` ud? Kig på, hvad `String[] args` mon er godt for.
