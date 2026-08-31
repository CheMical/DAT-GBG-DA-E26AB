# Metoder – del 2

## Beskrivelse

I går lærte vi, hvad en metode er: en navngivet kodeblok, som kan kaldes igen og igen. I dag tager vi det et skridt videre.

Metoder er ikke kun en måde at undgå gentagelse på. De gør koden mere læselig, nemmere at teste og lettere at udvide. Når vi arbejder os videre i Java, vil vi bruge metoder i stort set alle større programmer.

I dag fokuserer vi på de områder, der gør metoder virkelig nyttige i praksis:

* overloading
* scope
* `static`
* pass-by-value for primitive typer
* god metode-design

---

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

* forklare, hvad overloading er
* forklare, hvad scope betyder i Java
* forklare, hvorfor en lokal variabel ikke findes uden for sin metode eller blok
* forklare forskellen på `static` og instansmetoder
* forklare, hvorfor primitive værdier sendes videre som kopier
* skrive metoder, der kalder andre metoder
* refaktorisere kode fra `main` til tydelige hjælpemetoder
* vælge gode navne til metoder, så de beskriver præcis, hvad de gør

---

## Se disse videoer før undervisningen:

[methods](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=4h4m27s) (fra: 04:04:27 til: 04:19:51)  
[overloaded methods](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=4h19m51s) (til: 04:25:59)  
[variable scope](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=4h25m59s) (til: 04:30:57)  
[static](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=7h14m07s) (til: 07:22:04)

---

## Læs nedenstående før undervisningen

### 1. Repetition: metoder er genbrug med mening

En metode består af fire vigtige dele:

```java
public static int add(int a, int b) {
    return a + b;
}
```

* `public` = hvem må kalde metoden
* `static` = metoden hører til klassen, ikke et objekt
* `int` = returtype
* `add` = metode-navn
* `(int a, int b)` = parametre
* `{ ... }` = metode-kroppen
* `return a + b;` = den værdi, metoden sender tilbage

Hvis en metode ikke skal returnere noget, bruger vi `void`:

```java
public static void sayHello() {
    System.out.println("Hello!");
}
```

Det betyder: "denne metode gør noget, men den returnerer ingen værdi".

Metoder giver os:

1. genbrug
2. bedre navngivning
3. mere overskuelig kode
4. mindre risiko for fejl, når vi ændrer noget

Det vigtigste er måske dette:

> Når vi læser kode, læser vi ofte den flere gange – men skriver den kun én gang. Derfor er gode metoder en stor hjælp.

---

### 2. Overloading – flere metoder med samme navn

Java tillader flere metoder med samme navn, så længe de har forskellige parametre.

```java
public static int max(int a, int b) {
    if (a > b) {
        return a;
    }
    return b;
}

public static int max(int a, int b, int c) {
    int first = max(a, b);
    return max(first, c);
}
```

Når Java ser kaldet:

```java
System.out.println(max(5, 9));
System.out.println(max(2, 8, 4));
```

vælger den den metode, hvis parametre passer til argumenterne.

Det kaldes **overloading**.

Vigtigt:

* samme navn
* forskellige parametre
* returtypen alene er ikke nok

Dette er også grunden til, at `System.out.println()` kan håndtere mange forskellige typer:

```java
System.out.println(5);
System.out.println("Hej");
System.out.println(true);
System.out.println(3.14);
```

Der er faktisk flere forskellige `println`-metoder med samme navn.

---

### 3. Parameter vs. argument

Det er let at blande de to begreber sammen.

```java
public static int add(int a, int b) {   // a og b er PARAMETRE
    return a + b;
}
```

```java
int result = add(3, 5);                // 3 og 5 er ARGUMENTER
```

* En **parameter** er den variabel, metoden erklærer sig villig til at modtage.
* Et **argument** er den værdi, du faktisk sender med, når du kalder metoden.

Rækkefølgen betyder noget. Java kigger på placering, ikke på navnet.

```java
public static void printPerson(String name, int age) {
    System.out.println(name + " er " + age + " år");
}

printPerson("Anna", 25);      // korrekt
printPerson(25, "Anna");      // fejl
```

Det er derfor vigtigt at vælge gode parameternavne, så rækkefølgen bliver tydelig.

---

### 4. Scope – hvor findes en variabel?

En variabel findes kun i den blok eller metode, den er erklæret i.

```java
public static void doSomething() {
    int number = 5;
    System.out.println(number);
}

public static void main(String[] args) {
    doSomething();
    // System.out.println(number);   // fejl: number findes ikke her
}
```

Det samme gælder i en `if`-blok:

```java
if (true) {
    int x = 10;
}

// System.out.println(x); // fejl: x findes ikke uden for if-blokken
```

**Reglen:** en variabel findes fra den linje, den bliver erklæret, til den afsluttende `}` for dens blok.

Det er nyttigt, fordi hver metode får sit eget “rum”.

```java
public static void methodA() {
    int count = 5;
    System.out.println(count);
}

public static void methodB() {
    int count = 100;
    System.out.println(count);
}
```

Her er `count` ikke den samme variabel. Det er to forskellige variable med samme navn.

> Scope er en styrke, ikke en begrænsning. Det gør det nemmere at læse og fejlsøge en metode isoleret.

---

### 5. `static` – hvorfor kan `main` kalde andre metoder direkte?

I dag skriver vi normalt metoder som `static` i `Main`:

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

Det virker, fordi `main` er også `static`.

En `static` metode hører til klassen, ikke til et bestemt objekt.

```java
int result = Math.max(3, 7);
```

`Math.max` er `static`, så vi kan kalde den direkte på klassen `Math`.

Modsat har vi objekter:

```java
Scanner scanner = new Scanner(System.in);
int tal = scanner.nextInt();
```

Her kalder vi en metode på et objekt.

Kort sagt:

* `static` metode → kaldes på klassen
* ikke-`static` metode → kaldes på et objekt

Dette er vigtigt senere, når vi kommer til objektorienteret programmering.

---

### 6. Primitive typer er kopier

Metoder får en kopi af primitive værdier.

```java
public static void increase(int number) {
    number = number + 10;
    System.out.println("Inde i metoden: " + number);
}

public static void main(String[] args) {
    int myNumber = 5;
    increase(myNumber);
    System.out.println("Efter kaldet: " + myNumber);
}
```

Output:

```text
Inde i metoden: 15
Efter kaldet: 5
```

`myNumber` ændres ikke uden for metoden, fordi `number` er kun en kopi af værdien.

Hvis vi vil have ændringen tilbage, skal vi returnere en ny værdi:

```java
public static int increase(int number) {
    return number + 10;
}

int myNumber = 5;
myNumber = increase(myNumber);
```

Dette er en vigtig pointe, når vi arbejder med primitive typer i Java.

---

### 7. Metode-design: én metode – én opgave

Det vigtigste designprincip ved metoder er ikke teknisk – det er logisk:

> En metode skal gøre én ting, og navnet skal fortælle, hvad den gør.

Gode metoder har typisk:

* et tydeligt navn
* et kort stykke kode, som man kan overskue
* en enkelt ansvarlighed
* en kodeblok, der kan læses uden at skulle forstå resten af programmet

Eksempler:

```java
public static boolean isEven(int number) { ... }
public static double calculateAverage(int[] values) { ... }
public static void printFrame(String text) { ... }
```

Det er meget bedre end navne som:

```java
public static void doStuff(int[] a) { ... }
```

Når et navn er tydeligt, bliver koden meget lettere at forstå.

---

### 8. Refaktorisering: tag kode ud af `main`

Nogle gange begynder vi med al kode i `main`:

```java
public static void main(String[] args) {
    System.out.println("*******************");
    System.out.println("*   Velkommen!    *");
    System.out.println("*******************");

    // ... mere kode ...

    System.out.println("*******************");
    System.out.println("*    Farvel!      *");
    System.out.println("*******************");
}
```

Det bliver hurtigt uoverskueligt.

Vi kan løfte det ud i metoder:

```java
public static void printFrame(String text) {
    int width = text.length() + 4;

    printLine(width, '*');
    System.out.println("* " + text + " *");
    printLine(width, '*');
}

public static void main(String[] args) {
    printFrame("Velkommen!");

    // ... mere kode ...

    printFrame("Farvel!");
}
```

Det gør programmet mere læsbart og enklere at ændre.

---

### 9. Praktiske Java-eksempler

#### Eksempel 1: printLine

```java
public static void printLine(int length, char symbol) {
    for (int i = 0; i < length; i++) {
        System.out.print(symbol);
    }
    System.out.println();
}
```

Brug:

```java
printLine(10, '-');
printLine(5, '*');
```

#### Eksempel 2: printBox

```java
public static void printBox(String text) {
    int width = text.length() + 4;

    printLine(width, '*');
    System.out.println("* " + text + " *");
    printLine(width, '*');
}
```

#### Eksempel 3: metode der bruger andre metoder

```java
public static int square(int number) {
    return number * number;
}

public static int cube(int number) {
    return square(number) * number;
}
```

#### Eksempel 4: returnere en betinget værdi

```java
public static String describe(int number) {
    if (number > 0) {
        return "positive";
    } else if (number < 0) {
        return "negative";
    }
    return "zero";
}
```

#### Eksempel 5: finde maksimum med overloading

```java
public static int max(int a, int b) {
    if (a > b) {
        return a;
    }
    return b;
}

public static int max(int a, int b, int c) {
    return max(max(a, b), c);
}
```

Det er et godt eksempel på, hvordan metoder kan bygge videre på hinanden.

---

## Opgaver til anden halvdel

### Opgave 1 – Overloading

Skriv tre metoder med samme navn:

```java
public static int max(int a, int b)
public static int max(int a, int b, int c)
public static double max(double a, double b)
```

Hver metode skal returnere det største tal.

### Opgave 2 – Scope

Skriv en metode, som erklærer en lokal variabel. Prøv derefter at bruge den variabel uden for metoden.

Hvad sker der, og hvorfor?

### Opgave 3 – Metoder der kalder andre metoder

Skriv disse metoder:

```java
public static int square(int number)
public static int cube(int number)
public static int sumOfSquares(int a, int b)
```

Brug `square()` i begge de to andre metoder.

### Opgave 4 – Refaktorér din kode

Tag et lille program, hvor al kode ligger i `main`, og flyt logikken ud i hjælpemetoder som:

```java
printWelcome()
printFarewell()
printLine()
printFrame()
```

### Opgave 5 – Udfordring

Skriv et program, der viser en lille “menu” i konsollen.

Programmet skal opdeles i metoder, for eksempel:

```java
public static void printMenu()
public static int readChoice()
public static void handleChoice(int choice)
```

Målet er at holde `main` kort og let at læse.

---

## Det vigtigste at tage med

* en metode har en signatur: navn + parametre
* `void` betyder: metoden returnerer ingen værdi
* `return` afslutter metoden med det samme
* parametre er variabler i metoden, argumenter er værdier i kaldet
* en variabel findes kun i sin egen blok eller metode (**scope**)
* overloading betyder: flere metoder med samme navn, forskellige parametre
* `static` metoder hører til klassen
* primitive typer sendes som kopier til metoden
* en metods navn skal fortælle, hvad den gør
* gode metoder gør ofte kun én ting

---

## Hvornår bruger vi metoder?

Du skal tænke på metoder, når du har noget kode, der:

* gentager sig
* er svær at læse i `main`
* skal bruges flere steder
* bliver mere overskuelig, når det bliver opdelt
* beskriver en tydelig opgave eller handling

Et godt spørgsmål at stille sig selv er:

> Hvis jeg skulle give denne metode et navn, hvad ville jeg kalde den?

Hvis navnet bliver klart og præcist, er metoden næsten altid godt designet.

---

## Aktiviteter i undervisningen

Arbejd med de metoder, du har lært om i går, og brug dem til at strukturere og opbygge mere komplekse programmer.

Læg især mærke til:

* hvordan `main` bliver kortere
* hvordan `scope` forhindrer fejl
* hvordan metoder kan genbruges i stedet for at kopiere kode
* hvordan overloading kan gøre en klasse mere fleksibel

Det er her, Java begynder at blive rigtig struktureret og læsbart.
