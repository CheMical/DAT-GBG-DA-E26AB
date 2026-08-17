# Metoder

## Beskrivelse

Indtil nu har vi skrevet det meste af vores kode i `main`. Det virker fint til små programmer – men
det holder ikke ret længe.

I dag lærer vi at dele koden op i **metoder**: navngivne stykker kode, som vi kan kalde, når vi har
brug for dem. En metode kan modtage værdier ind (**parametre**) og sende en værdi tilbage
(**return**).

Metoder er den vigtigste enkeltting i objektorienteret programmering. Alt, hvad et objekt kan,
udtrykkes som metoder – så det, vi lærer i dag, bruger vi resten af uddannelsen.

Du er allerede stødt på metoder i denne uge, da vi lavede klasser og objekter. I dag går vi
grundigt til værks.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* skrive en metode med og uden parametre
* skrive en metode med og uden returværdi
* forklare forskellen på `void` og en returtype
* kalde en metode og bruge den værdi, den returnerer
* forklare forskellen på en **parameter** og et **argument**
* forklare hvad **scope** er, og hvorfor en lokal variabel ikke findes uden for sin metode
* overloade en metode, og forklare hvordan Java vælger den rigtige
* forklare hvorfor `main` er `static`, og hvad det betyder for de metoder, den kan kalde
* dele et program op i metoder, der hver især gør én ting

## Se disse videoer før undervisningen:

[methods](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=4h4m27s) (til: 04:19:51)
[overloaded methods](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=4h19m51s) (til: 04:25:59)
[variable scope](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=4h25m59s) (til: 04:30:57)

## Læs nedenstående før undervisningen

---

<img src="images/antikythera.jpg" alt="Antikythera-mekanismen, tandhjul i korroderet bronze" width="260" align="right">

### Hvorfor metoder?

Se på dette program:

```java
public static void main(String[] args) {

    System.out.println("*******************");
    System.out.println("*   Velkommen!    *");
    System.out.println("*******************");

    // ... en masse kode ...

    System.out.println("*******************");
    System.out.println("*    Farvel!      *");
    System.out.println("*******************");
}
```

Rammen bliver tegnet to gange. Skal vi ændre den, skal vi rette to steder – og hvis den optræder ti
steder, ti steder.

Med en metode skriver vi den én gang:

```java
public static void printFrame(String text) {
    System.out.println("*******************");
    System.out.println("*   " + text);
    System.out.println("*******************");
}
```

og bruger den, hvor vi har brug for den:

```java
public static void main(String[] args) {

    printFrame("Velkommen!");

    // ... en masse kode ...

    printFrame("Farvel!");
}
```

Metoder giver os tre ting:

1. **Genbrug** – skriv én gang, brug mange gange
2. **Navngivning** – `printFrame(...)` fortæller, hvad der sker, uden at man skal læse koden
3. **Overblik** – `main` bliver kort og læselig

Den anden er faktisk den vigtigste. Kode læses langt oftere, end den skrives.

---

### En metodes dele

```java
public static int add(int a, int b) {
    return a + b;
}
```

| Del | Her | Betyder |
| --- | --- | --- |
| access modifier | `public` | hvem må kalde metoden |
| `static` | `static` | metoden hører til klassen, ikke et objekt |
| returtype | `int` | hvilken slags værdi metoden giver tilbage |
| navn | `add` | hvad metoden hedder |
| parameterliste | `(int a, int b)` | hvad metoden skal have med |
| krop | `{ return a + b; }` | hvad metoden gør |

Metoden kaldes sådan:

```java
int result = add(3, 5);

System.out.println(result);
```

Output:

```text
8
```

---

### `void` – en metode uden returværdi

Nogle metoder skal ikke give noget tilbage. De gør bare noget:

```java
public static void sayHello() {
    System.out.println("Hello!");
}
```

`void` betyder "intet". Metoden kaldes sådan:

```java
sayHello();
```

Man kan **ikke** gemme resultatet af en `void`-metode:

```java
String greeting = sayHello();   // ← fejl
```

Der er jo ikke noget at gemme.

---

### `return` – send en værdi tilbage

```java
public static int square(int number) {
    return number * number;
}
```

```java
int result = square(4);

System.out.println(result);
```

Output:

```text
16
```

Tre ting om `return`:

**1. `return` afslutter metoden med det samme.** Kode efter et `return` bliver aldrig kørt:

```java
public static int square(int number) {
    return number * number;

    System.out.println("Dette bliver aldrig kørt");   // ← fejl fra compileren
}
```

**2. Returtypen skal passe.** Er returtypen `int`, skal du returnere en `int`:

```java
public static int square(int number) {
    return "hello";        // ← fejl
}
```

**3. Alle veje gennem metoden skal returnere noget:**

```java
public static String describe(int number) {

    if (number > 0) {
        return "positive";
    }
    // ← fejl: hvad hvis number ikke er > 0?
}
```

Compileren siger `missing return statement`. Ret det med et `else` eller et `return` til sidst:

```java
public static String describe(int number) {

    if (number > 0) {
        return "positive";
    }

    return "not positive";
}
```

---

### Man kan godt returnere fra flere steder

Det er helt i orden – og ofte klarere:

```java
public static String grade(int score) {

    if (score >= 90) {
        return "A";
    }

    if (score >= 80) {
        return "B";
    }

    if (score >= 70) {
        return "C";
    }

    return "F";
}
```

Man kan også bruge `return;` alene i en `void`-metode til at hoppe ud tidligt:

```java
public static void printIfPositive(int number) {

    if (number <= 0) {
        return;
    }

    System.out.println(number);
}
```

---

### Parametre og argumenter

De to ord bruges tit i flæng, men de betyder to forskellige ting:

```java
public static int add(int a, int b) {    // a og b er PARAMETRE
    return a + b;
}
```

```java
int result = add(3, 5);                  // 3 og 5 er ARGUMENTER
```

* En **parameter** er den variabel, metoden erklærer, at den vil have.
* Et **argument** er den værdi, du giver med, når du kalder.

Rækkefølgen betyder alt. Java kigger ikke på navnene, kun på pladserne:

```java
public static void printPerson(String name, int age) {
    System.out.println(name + " er " + age + " år");
}
```

```java
printPerson("Anna", 25);      // rigtigt
printPerson(25, "Anna");      // ← fejl: typerne passer ikke
```

Og her går det galt uden at compileren opdager det:

```java
public static void divide(int numerator, int denominator) {
    System.out.println(numerator / denominator);
}
```

```java
divide(2, 10);     // giver 0 – mente du divide(10, 2)?
```

> Derfor: giv dine parametre navne, der gør rækkefølgen indlysende.

---

### Parametre er kopier

Se på dette:

```java
public static void increase(int number) {
    number = number + 10;
    System.out.println("Inde i metoden: " + number);
}
```

```java
int myNumber = 5;

increase(myNumber);

System.out.println("Efter kaldet: " + myNumber);
```

Output:

```text
Inde i metoden: 15
Efter kaldet: 5
```

`myNumber` blev ikke ændret. Metoden fik en **kopi** af værdien.

Vil du have en ændret værdi ud af en metode, skal du **returnere** den:

```java
public static int increase(int number) {
    return number + 10;
}
```

```java
int myNumber = 5;

myNumber = increase(myNumber);

System.out.println(myNumber);      // 15
```

> Det gælder for primitive typer (`int`, `double`, `boolean`, `char`). For **objekter** opfører det
> sig anderledes – og det er præcis dét, vi kommer til at bruge i Adventure-projektet i uge 39.
> Læg mærke til denne pointe nu; vi vender tilbage til den.

---

### Scope – hvor findes en variabel?

En variabel, der er oprettet inde i en metode, findes **kun** der:

```java
public static void doSomething() {
    int number = 5;
}

public static void main(String[] args) {
    doSomething();

    System.out.println(number);    // ← fejl: number findes ikke her
}
```

Det samme gælder inde i en blok:

```java
if (true) {
    int x = 10;
}

System.out.println(x);      // ← fejl
```

**Reglen:** en variabel findes fra det sted, den erklæres, til den afsluttende `}` for den blok,
den står i.

To metoder kan sagtens bruge det samme variabelnavn uden at forstyrre hinanden:

```java
public static void methodA() {
    int count = 5;
    System.out.println(count);      // 5
}

public static void methodB() {
    int count = 100;
    System.out.println(count);      // 100
}
```

Det er ikke den samme variabel. Det er to forskellige, der tilfældigvis hedder det samme.

> Scope er en fordel, ikke en begrænsning. Det betyder, at du kan læse en metode isoleret og vide,
> at ingen andre roder med dens variable.

---

### Overloading – flere metoder med samme navn

Java tillader flere metoder med samme navn, så længe **parametrene er forskellige**:

```java
public static int add(int a, int b) {
    return a + b;
}

public static int add(int a, int b, int c) {
    return a + b + c;
}

public static double add(double a, double b) {
    return a + b;
}
```

```java
System.out.println(add(2, 3));          // 5      → første
System.out.println(add(2, 3, 4));       // 9      → anden
System.out.println(add(2.5, 3.5));      // 6.0    → tredje
```

Java vælger den metode, hvis parametre passer til de argumenter, du giver med. Det kaldes
**overloading**.

Du har allerede brugt det uden at vide det:

```java
System.out.println(5);
System.out.println("hello");
System.out.println(true);
System.out.println(3.14);
```

Det er ikke én metode, der kan alt. Det er mange forskellige `println`-metoder med samme navn.

**Returtypen alene er ikke nok.** Dette virker ikke:

```java
public static int getValue() { return 5; }
public static double getValue() { return 5.0; }     // ← fejl
```

Java kan ikke se på kaldet `getValue()`, hvilken af dem du mente.

---

### Hvorfor står der `static`?

Det korte svar for i dag: `main` er `static`, og en `static` metode kan kun kalde andre `static`
metoder direkte. Så når du skriver hjælpemetoder, som `main` skal bruge, skal de også være
`static`:

```java
public class Main {

    public static void main(String[] args) {
        System.out.println(square(4));
    }

    public static int square(int number) {
        return number * number;
    }
}
```

Det lange svar hænger sammen med objekter: en **ikke**-static metode hører til et *objekt* og skal
kaldes på et objekt:

```java
Book book = new Book("The Hobbit", "Tolkien", 1937);

book.printInfo();          // metode på et objekt – ikke static
```

En `static` metode hører til *klassen* og kaldes uden objekt:

```java
int result = Math.max(3, 7);     // Math.max er static
```

I [bogsamlingsprojektet](../../projekter/bogsamling/readme.md) skriver du metoder på objekter. I
dagens opgaver skriver vi `static` metoder i `Main`, så vi kan koncentrere os om selve
metode-begrebet.

---

### Én metode – én opgave

Den vigtigste regel om metoder er ikke teknisk, men designmæssig:

> **En metode skal gøre én ting, og navnet skal fortælle hvilken.**

Kan du ikke give metoden et kort, præcist navn, gør den formentlig for meget.

Kendetegn ved en god metode:

* et navn, der er et **udsagnsord**: `calculateTotal`, `findBook`, `isValid`, `printReport`
* den er kort nok til at kunne ses på skærmen på én gang
* den kan forstås uden at man skal kigge på resten af programmet
* hvis den returnerer en `boolean`, hedder den typisk `isSomething` eller `hasSomething`

Sammenlign:

```java
public static void doStuff(int[] a) { ... }
```

med:

```java
public static double calculateAverage(int[] grades) { ... }
```

Den nederste kan man bruge uden at læse dens kode.

---

### Kan du forudsige resultatet?

#### Eksempel 1

```java
public static int triple(int number) {
    return number * 3;
}

public static void main(String[] args) {
    System.out.println(triple(4));
    System.out.println(triple(triple(2)));
}
```

#### Eksempel 2

```java
public static void addTen(int number) {
    number += 10;
}

public static void main(String[] args) {
    int value = 5;
    addTen(value);
    System.out.println(value);
}
```

#### Eksempel 3

```java
public static int mystery(int a, int b) {
    if (a > b) {
        return a;
    }
    return b;
}

public static void main(String[] args) {
    System.out.println(mystery(3, 9));
    System.out.println(mystery(9, 3));
    System.out.println(mystery(4, 4));
}
```

> Hvad ville du kalde `mystery`, hvis du skulle give den et ordentligt navn?

#### Eksempel 4

```java
public static void main(String[] args) {
    System.out.println(add(1, 2));
    System.out.println(add(1.0, 2.0));
}

public static int add(int a, int b) {
    System.out.println("int-versionen");
    return a + b;
}

public static double add(double a, double b) {
    System.out.println("double-versionen");
    return a + b;
}
```

#### Eksempel 5

```java
public static int count() {
    int number = 0;
    number++;
    return number;
}

public static void main(String[] args) {
    System.out.println(count());
    System.out.println(count());
    System.out.println(count());
}
```

> Hvorfor bliver tallet ikke ved med at vokse?

---

## Det vigtigste at tage med

* en metode har: returtype, navn, parametre og en krop
* `void` betyder "returnerer ingenting"
* `return` afslutter metoden **med det samme**
* alle veje gennem en metode med returtype skal returnere noget
* **parameter** = i erklæringen, **argument** = i kaldet
* rækkefølgen af argumenter betyder alt
* primitive parametre er **kopier** – metoden kan ikke ændre kalderens variabel
* en variabel findes kun i sin egen blok (**scope**)
* **overloading**: samme navn, forskellige parametre – returtypen alene er ikke nok
* `main` er `static`, så de metoder den kalder direkte, skal også være `static`
* én metode, én opgave – og et navn der siger hvilken

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md)
