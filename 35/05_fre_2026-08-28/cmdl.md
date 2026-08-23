# Brugerinput fra kommandolinjen

## Beskrivelse

Indtil nu har vores programmer haft alle værdier skrevet direkte ind i koden. Nu lærer vi at
**tage imod input fra brugeren**, mens programmet kører.

Vi bruger klassen `Scanner` fra Javas standardbibliotek til at læse tekst og tal, som brugeren
skriver i terminalen.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* importere `Scanner` med `import java.util.Scanner;`
* oprette et `Scanner`-objekt der læser fra `System.in`
* bruge `scanner.nextLine()` til at læse en linje tekst
* bruge `scanner.nextInt()` til at læse et heltal
* kombinere `System.out.print()` og `Scanner` til en simpel dialog med brugeren
* køre et Java-program med brugerinput fra terminalen
* angive programargumenter i IntelliJ IDEA

---

## Hvad er `Scanner`?

`Scanner` er en klasse, der gør det nemt at læse input – fra tastaturet, fra en fil eller fra en
streng. I dag bruger vi den til at læse fra **standard input** (`System.in`), som er tastaturet i
terminalen.

Inden du kan bruge `Scanner`, skal du fortælle Java, at du vil bruge den. Det gør du med en
**import**-sætning øverst i filen, inden `public class ...`:

```java
import java.util.Scanner;
```

Derefter opretter du et `Scanner`-objekt:

```java
Scanner scanner = new Scanner(System.in);
```

Nu kan du bruge `scanner` til at læse input:

```java
String name = scanner.nextLine();
```

---

## Et simpelt eksempel

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Hvad hedder du? ");
        String name = scanner.nextLine();

        System.out.println("Hej, " + name + "!");

    }
}
```

Bemærk at vi bruger `System.out.print` (uden `ln`) til spørgsmålet, så cursoren bliver på
samme linje som det brugeren skriver.

### Eksempel med et tal

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Indtast et tal: ");
        int number = scanner.nextInt();

        System.out.println("Du indtastede: " + number);
        System.out.println("Det dobbelte er: " + (number * 2));

    }
}
```

---

## Kør programmet fra terminalen

Nedenfor er en illustration af, hvordan en session kan se ud i terminalen. De linjer der starter
med `$` er kommandoer; resten er output fra programmet eller brugerens input.

```
$ javac Main.java
$ java Main
Hvad hedder du? Anna
Hej, Anna!
```

### Trin-for-trin

1. Åbn en terminal og naviger til den mappe, der indeholder din `.java`-fil.
2. Kompilér med:
   ```
   javac Main.java
   ```
3. Kør det kompilerede program med:
   ```
   java Main
   ```
4. Programmet venter nu på input. Skriv dit svar og tryk **Enter**.

> **Tip:** Sørg for at du er i den rigtige mappe. Brug `cd` til at skifte mappe og `ls` (macOS /
> Linux) eller `dir` (Windows) til at se, hvad der er i mappen.

---

## Kør programmet i IntelliJ IDEA

I IntelliJ kan du køre programmet direkte med den grønne **Run**-knap (▶). IntelliJ åbner et
**Run**-panel nederst i vinduet, og der kan du skrive dit input præcis som i en rigtig terminal.

### Sådan giver du programargumenter i IntelliJ

Programargumenter (`args` i `main(String[] args)`) er ikke det samme som `Scanner`-input – de
angives *inden* programmet starter. Sådan gør du:

1. Klik på **Run** i menulinjen → **Edit Configurations…**
2. Vælg din konfiguration (typisk `Main`) i listen til venstre.
3. Find feltet **Program arguments**.
4. Skriv de argumenter du vil sende til programmet, adskilt af mellemrum.
5. Klik **OK** og kør programmet.

Argumenterne kan du derefter læse i din kode via `args`-arrayet:

```java
public class Main {

    public static void main(String[] args) {

        if (args.length > 0) {
            System.out.println("Første argument: " + args[0]);
        } else {
            System.out.println("Ingen argumenter givet.");
        }

    }
}
```

### Scanner-input i IntelliJ

Når du bruger `Scanner(System.in)` og klikker **Run**, åbner IntelliJ et **Run**-panel. Programmet
pauser, når det venter på input. Klik i panelet og skriv dit svar, derefter **Enter** – præcis som
i terminalen.

---

## Hyppige fejl

| Fejl | Årsag | Løsning |
|------|-------|---------|
| `Exception in thread "main" java.util.NoSuchElementException` | `scanner.nextInt()` fandt ikke et tal | Tjek at du faktisk skriver et tal og trykker Enter |
| `Exception ... InputMismatchException` | Brugeren skrev tekst, men koden forventede et tal | Brug `nextLine()` til tekst og `nextInt()` til heltal |
| Programmet stopper uden at vente på input | `Scanner` er ikke oprettet, eller `nextLine()` mangler | Tjek at `scanner = new Scanner(System.in)` er der |

---

## Det vigtigste at tage med

* Importer `Scanner` med `import java.util.Scanner;`
* Opret `Scanner scanner = new Scanner(System.in);`
* Brug `scanner.nextLine()` til tekst og `scanner.nextInt()` til heltal
* I terminalen: kompilér med `javac`, kør med `java`
* I IntelliJ: skriv Scanner-input direkte i Run-panelet; programargumenter sættes under
  **Run → Edit Configurations → Program arguments**

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md)
