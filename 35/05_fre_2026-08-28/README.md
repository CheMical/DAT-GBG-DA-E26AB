# I/O: Scanner og print samt statustjek for bruger på Github

## Beskrivelse

I denne lektion arbejder vi med **input og output** i Java.

Indtil nu har vores programmer mest skrevet tekst ud i konsollen. Nu lærer vi, hvordan et program
også kan **læse input fra brugeren**, så vi kan lave små interaktive programmer.

Vi arbejder med `System.out.print`, `System.out.println` og `Scanner`.

> **Bemærk:** Vi arbejder kun med helt enkle programmer i dag. Vi bruger **ikke** løkker endnu.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* forklare hvad **input** og **output** er
* bruge `System.out.print()` og `System.out.println()`
* oprette en `Scanner` og læse input fra brugeren
* læse tekst med `nextLine()`
* læse tal med `nextInt()` og `nextDouble()`
* kombinere input og output i et lille program
* forstå forskellen på `print()` og `println()`

## Se disse videoer før undervisninge

[Brugerinput](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=31m30s) (til: 00:47:25)

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

## Hvad er output?

Når et program skriver noget til skærmen, kalder vi det **output**.

I Java bruger vi ofte:

```java
System.out.println("Hello, world!");
```

Det skriver tekst ud i konsollen og hopper bagefter ned på en ny linje.

Eksempel:

```java
System.out.println("Hej");
System.out.println("med dig");
```

Output:

```text
Hej
med dig
```

---

## `print` og `println`

Der er to meget almindelige måder at skrive tekst ud på:

```java
System.out.print("Hej ");
System.out.print("med dig");
```

Output:

```text
Hej med dig
```

Forskellen er:

* `print()` skriver uden at hoppe til ny linje
* `println()` skriver og hopper til ny linje

Eksempel:

```java
System.out.print("A");
System.out.print("B");
System.out.println("C");
System.out.println("D");
```

Output:

```text
ABC
D
```

---

## Hvad er input?

Når programmet læser noget, som brugeren skriver, kalder vi det **input**.

I Java bruger vi ofte klassen `Scanner` til at læse input fra konsollen.

Først skal vi importere den:

```java
import java.util.Scanner;
```

Derefter kan vi oprette en `Scanner`:

```java
Scanner scanner = new Scanner(System.in);
```

`System.in` betyder, at vi læser fra tastaturet.

---

## Læs tekst med `nextLine()`

Hvis vi vil læse en hel linje tekst, bruger vi `nextLine()`.

Eksempel:

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Hvad hedder du? ");
        String name = scanner.nextLine();

        System.out.println("Hej " + name);
    }
}
```

Hvis brugeren skriver `Sofie`, bliver output:

```text
Hvad hedder du? Sofie
Hej Sofie
```

---

## Læs heltal med `nextInt()`

Hvis vi vil læse et helt tal, bruger vi `nextInt()`.

Eksempel:

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Hvor gammel er du? ");
        int age = scanner.nextInt();

        System.out.println("Du er " + age + " år gammel");
    }
}
```

Hvis brugeren skriver `21`, bliver output:

```text
Hvor gammel er du? 21
Du er 21 år gammel
```

---

## Læs decimaltal med `nextDouble()`

Hvis vi vil læse et decimaltal, bruger vi `nextDouble()`.

Eksempel:

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Hvor høj er du? ");
        double height = scanner.nextDouble();

        System.out.println("Du er " + height + " meter høj");
    }
}
```

Hvis brugeren skriver `1.72`, bliver output:

```text
Hvor høj er du? 1.72
Du er 1.72 meter høj
```

> Husk: Java bruger **punktum** som decimaltegn.

---

## Et samlet eksempel

Her er et lille program, der spørger om navn og alder:

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Hvad hedder du? ");
        String name = scanner.nextLine();

        System.out.print("Hvor gammel er du? ");
        int age = scanner.nextInt();

        System.out.println("Hej " + name);
        System.out.println("Du er " + age + " år gammel");
    }
}
```

---

## Hvad sker der bag kulisserne?

Når du skriver:

```java
Scanner scanner = new Scanner(System.in);
```

så fortæller du Java, at programmet skal kunne læse fra tastaturet.

Når du derefter skriver:

```java
String name = scanner.nextLine();
```

så venter programmet på, at brugeren skriver noget og trykker Enter.

Det er altså brugeren, der bestemmer værdien.

---

## Vigtige ting at huske

* `print()` skriver uden ny linje
* `println()` skriver med ny linje
* `Scanner` bruges til at læse input
* `nextLine()` læser tekst
* `nextInt()` læser heltal
* `nextDouble()` læser decimaltal

---

## Prøv selv

Lav et lille program, der spørger brugeren om:

* navn
* alder
* yndlingsfarve

og skriver det pænt ud bagefter.

Eksempel:

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Hvad hedder du? ");
        String name = scanner.nextLine();

        System.out.print("Hvor gammel er du? ");
        int age = scanner.nextInt();

        System.out.print("Hvad er din yndlingsfarve? ");
        String color = scanner.nextLine();

        System.out.println("Navn: " + name);
        System.out.println("Alder: " + age);
        System.out.println("Yndlingsfarve: " + color);
    }
}
```

> Tip: I nogle tilfælde kan `nextInt()` og `nextDouble()` efterlade en linjeskiftkarakter i input,
> så man skal være opmærksom på det. Det kigger vi nærmere på senere.

---

## Det vigtigste at tage med

Efter denne forberedelse skal du især kunne:

* forklare forskellen på input og output
* bruge `System.out.print()` og `System.out.println()`
* oprette en `Scanner`
* læse tekst med `nextLine()`
* læse tal med `nextInt()` og `nextDouble()`
* lave små programmer, der spørger brugeren om information og skriver et svar tilbage

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md)

Statustjek for oprettelse af bruger på Github:
* Tænke på at finde et passende brugernavn inden undervisningen, hvis du ikke allerede er oprettet.
