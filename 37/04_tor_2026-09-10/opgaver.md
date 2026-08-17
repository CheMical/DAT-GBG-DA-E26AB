# Opgaver – Metoder

I disse opgaver skal du skrive metoder: med og uden parametre, med og uden returværdi.

## Kom i gang

Opret en klasse `Main`. Alle metoder i dag skrives som `static` metoder i `Main`, **uden for**
`main`-metoden – men inde i klassen:

```java
public class Main {

    public static void main(String[] args) {
        // her kalder du dine metoder
    }

    // her skriver du dine metoder
    public static void sayHello() {
        System.out.println("Hello!");
    }
}
```

**Afprøv hver metode fra `main`, efterhånden som du skriver den.** En metode, der ikke er kaldt, er
ikke testet.

---

## Del 1 – De første metoder

### Opgave 1 – Uden parametre, uden returværdi

Skriv en metode:

```java
public static void sayHello()
```

Den skal udskrive `Hello!`.

Kald den tre gange fra `main`.

### Opgave 2 – Med parameter

Skriv en metode:

```java
public static void greet(String name)
```

Den skal udskrive `Hello, <navn>!`.

Kald den med tre forskellige navne.

```text
Hello, Anna!
Hello, Mikkel!
Hello, Sofie!
```

### Opgave 3 – Med returværdi

Skriv en metode:

```java
public static int square(int number)
```

Den skal returnere tallet ganget med sig selv.

Afprøv i `main`:

```java
System.out.println(square(4));
System.out.println(square(7));

int result = square(3);
System.out.println(result);
```

### Opgave 4 – To parametre

Skriv en metode:

```java
public static int add(int a, int b)
```

der returnerer summen.

Skriv tilsvarende metoder til `subtract`, `multiply` og `divide`.

Overvej: hvad skal `divide` gøre, hvis nævneren er `0`? Prøv det, og se hvad der sker.

### Opgave 5 – Returnér en boolean

Skriv en metode:

```java
public static boolean isEven(int number)
```

der returnerer `true`, hvis tallet er lige.

Brug den i `main`:

```java
if (isEven(8)) {
    System.out.println("8 er lige");
}
```

Skriv den derefter om, så kroppen kun er én linje.

### Opgave 6 – Returnér en String

Skriv en metode:

```java
public static String describe(int number)
```

der returnerer `"positive"`, `"negative"` eller `"zero"`.

Afprøv med tre forskellige tal.

---

## Del 2 – Metoder der bruger hinanden

### Opgave 7 – Byg videre

Skriv disse tre metoder:

```java
public static int square(int number)
public static int cube(int number)
public static int sumOfSquares(int a, int b)
```

`cube` skal bruge `square`. `sumOfSquares` skal bruge `square` to gange.

Skriv **ikke** `number * number` mere end ét sted i hele programmet.

### Opgave 8 – Største af tre

Skriv en metode:

```java
public static int max(int a, int b)
```

der returnerer det største af to tal.

Skriv derefter:

```java
public static int max(int a, int b, int c)
```

der returnerer det største af tre tal – ved at bruge den første metode to gange.

> Læg mærke til: dette er overloading. To metoder med samme navn og forskellige parametre.

### Opgave 9 – Rammen

Skriv en metode:

```java
public static void printFrame(String text)
```

der udskriver en ramme omkring teksten:

```text
*****************
*   Velkommen   *
*****************
```

Rammen skal tilpasse sig tekstens længde. Brug `text.length()` og et loop.

### Opgave 10 – En linje

Skriv en metode:

```java
public static void printLine(int length, char symbol)
```

der udskriver en linje af det angivne symbol:

```java
printLine(10, '-');     // ----------
printLine(5, '*');      // *****
```

Brug den i din løsning til opgave 9.

---

## Del 3 – Metoder og arrays

### Opgave 11 – Sum af array

Skriv en metode:

```java
public static int sum(int[] numbers)
```

der returnerer summen af alle tal i arrayet.

### Opgave 12 – Gennemsnit

Skriv en metode:

```java
public static double average(int[] numbers)
```

der returnerer gennemsnittet. Den skal bruge `sum` fra opgave 11.

Pas på heltalsdivision.

### Opgave 13 – Største i array

Skriv:

```java
public static int max(int[] numbers)
```

der returnerer det største tal i arrayet.

> Bemærk at dette også er overloading – du har nu tre `max`-metoder.

### Opgave 14 – Søg i array

Skriv:

```java
public static int indexOf(int[] numbers, int target)
```

der returnerer index for første forekomst af `target`, eller `-1` hvis den ikke findes.

Skriv også:

```java
public static boolean contains(int[] numbers, int target)
```

der returnerer `true`/`false`. Lad den bruge `indexOf`.

### Opgave 15 – Udskriv array

Skriv:

```java
public static void printArray(int[] numbers)
```

der udskriver arrayet pænt på én linje:

```text
[12, 45, 7, 23]
```

Pas på det sidste komma.

---

## Del 4 – Overloading

### Opgave 16 – Tre versioner af greet

Skriv tre metoder med samme navn:

```java
public static void greet()                              // "Hello!"
public static void greet(String name)                   // "Hello, Anna!"
public static void greet(String name, String language)  // "Hej, Anna!" ved language = "dansk"
```

Kald alle tre fra `main`.

### Opgave 17 – Hvilken bliver valgt?

Skriv disse to metoder:

```java
public static void show(int number) {
    System.out.println("int: " + number);
}

public static void show(double number) {
    System.out.println("double: " + number);
}
```

Kald dem med:

```java
show(5);
show(5.0);
show(5.5);
```

Hvad blev skrevet ud? Kunne du forudsige det?

### Opgave 18 – Når det ikke kan lade sig gøre

Prøv at skrive disse to metoder i samme klasse:

```java
public static int getValue() {
    return 5;
}

public static double getValue() {
    return 5.0;
}
```

1. Hvad siger compileren?
2. Hvorfor kan Java ikke finde ud af det?

---

## Del 5 – Scope og parametre

### Opgave 19 – Kopien

Kør denne kode:

```java
public static void addTen(int number) {
    number += 10;
    System.out.println("Inde i metoden: " + number);
}

public static void main(String[] args) {
    int value = 5;
    addTen(value);
    System.out.println("Efter kaldet: " + value);
}
```

1. Hvad blev skrevet ud?
2. Hvorfor blev `value` ikke ændret?
3. Skriv `addTen` om, så den **returnerer** det nye tal, og brug den korrekt i `main`.

### Opgave 20 – Find fejlen

```java
public static void calculate() {
    int result = 5 * 3;
}

public static void main(String[] args) {
    calculate();
    System.out.println(result);
}
```

1. Hvad siger compileren?
2. Forklar hvorfor med ordet *scope*.
3. Ret det på to forskellige måder.

### Opgave 21 – Find fejlen

```java
public static int describe(int number) {

    if (number > 0) {
        return 1;
    }
    else if (number < 0) {
        return -1;
    }
}
```

1. Hvad siger compileren?
2. Hvad mangler der?
3. Ret det.

### Opgave 22 – Find fejlen

```java
public static void printSum(int a, int b) {
    return a + b;
}
```

1. Hvad er galt?
2. Ret det på to måder: én hvor metoden forbliver `void`, og én hvor den returnerer.

---

## Del 6 – Ryd op i et program

### Opgave 23 – Del det op

Her er et program, hvor alt står i `main`. Del det op i metoder.

```java
public static void main(String[] args) {

    int[] grades = {12, 7, 4, 10, 2, 12, 7, 0, 10, 4};

    int sum = 0;
    for (int i = 0; i < grades.length; i++) {
        sum += grades[i];
    }

    double average = (double) sum / grades.length;

    int max = grades[0];
    for (int i = 1; i < grades.length; i++) {
        if (grades[i] > max) {
            max = grades[i];
        }
    }

    int min = grades[0];
    for (int i = 1; i < grades.length; i++) {
        if (grades[i] < min) {
            min = grades[i];
        }
    }

    int passed = 0;
    for (int i = 0; i < grades.length; i++) {
        if (grades[i] >= 2) {
            passed++;
        }
    }

    System.out.println("Sum: " + sum);
    System.out.println("Gennemsnit: " + average);
    System.out.println("Højeste: " + max);
    System.out.println("Laveste: " + min);
    System.out.println("Bestået: " + passed);
}
```

Krav:

* `main` skal til sidst være under 10 linjer
* hver metode skal gøre **én** ting
* hver metode skal have et navn, der siger, hvad den gør
* du må gerne bruge de metoder, du allerede har skrevet i del 3

Sammenlign din opdeling med sidemandens. Har I valgt de samme metoder?

---

## Udfordring 1 – Et lille bibliotek

Skriv en samling metoder til tekst:

```java
public static int countVowels(String text)
public static String reverse(String text)
public static boolean isPalindrome(String text)
public static String capitalize(String text)       // "hello" → "Hello"
public static int countWords(String text)
```

Lad `isPalindrome` bruge `reverse`.

Test dem alle fra `main`, og skriv resultatet ud i en pæn oversigt.

---

## Udfordring 2 – Rekursion

En metode må gerne kalde **sig selv**. Det kaldes *rekursion*.

```java
public static int factorial(int n) {

    if (n <= 1) {
        return 1;
    }

    return n * factorial(n - 1);
}
```

1. Kør `factorial(5)`. Hvad giver den?
2. Tegn på papir, hvad der sker, når `factorial(5)` kaldes. Hvor mange gange kaldes metoden?
3. Hvad sker der, hvis du fjerner `if`-sætningen? Prøv det – hvad hedder fejlen?

Skriv derefter selv:

```java
public static int sumTo(int n)        // 1 + 2 + 3 + ... + n
public static int fibonacci(int n)    // 0, 1, 1, 2, 3, 5, 8, 13, ...
```

> Rekursion er ikke pensum lige nu, men det er godt at have set. Vi kommer tilbage til det.

---

## Udfordring 3 – Terningespil med metoder

Lav et lille spil:

* to spillere slår hver to terninger
* den med den højeste sum vinder runden
* der spilles fem runder
* til sidst skrives den samlede vinder

Krav: `main` må kun indeholde kald til metoder. Al logik skal ligge i metoder som:

```java
public static int rollDie()
public static int rollTwoDice()
public static String findRoundWinner(int player1, int player2)
public static void printResult(int score1, int score2)
```

Til terningerne:

```java
import java.util.Random;

Random random = new Random();
int die = random.nextInt(6) + 1;
```
