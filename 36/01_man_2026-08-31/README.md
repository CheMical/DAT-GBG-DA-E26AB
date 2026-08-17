# While-loops

## Beskrivelse

I denne lektion arbejder vi med **while-loops** i Java.

Et while-loop bruges, når vi ønsker at gentage noget, **så længe en bestemt betingelse er opfyldt**. Det er især nyttigt, når vi ikke på forhånd ved præcis, hvor mange gange noget skal gentages.

Vi ser også kort på `do-while` og forskellen mellem `while` og `do-while`.

## Læringsmål

* at kunne bruge `while`-loops
* at kunne forklare, hvordan betingelsen i et `while`-loop styrer gentagelsen
* at kunne bruge en tæller i et `while`-loop
* at kende forskel på `while` og `do-while`
* at kunne identificere et uendeligt loop

## Se disse videoer før undervisningen:

[While loops](https://www.youtube.com/watch?v=xk4_1vDrzzo) (til: 03:33:47)

[number guessing game](https://www.youtube.com/watch?v=xk4_1vDrzzo) (til: 03:43:33)

## Indhold

### Gentagelser i programmer

Vi har ofte brug for at udføre den samme kode flere gange.

Vi kunne eksempelvis skrive:

```java
System.out.println("Hej");
System.out.println("Hej");
System.out.println("Hej");
```

Men hvis noget skal gentages mange gange, bliver det hurtigt besværligt.

Her kan vi bruge et **loop**.

Et `while`-loop gentager noget, **så længe en betingelse er `true`**.

---

### Et simpelt while-loop

Et `while`-loop har denne grundform:

```java
while (betingelse) {
    // kode der skal gentages
}
```

Et simpelt eksempel:

```java
int number = 1;

while (number <= 5) {
    System.out.println(number);
    number++;
}
```

Programmet skriver:

```text
1
2
3
4
5
```

Vi kan læse koden som:

> Så længe `number` er mindre end eller lig med 5, skal koden mellem `{ }` udføres.

---

### Hvordan virker loopet?

Se igen på eksemplet:

```java
int number = 1;

while (number <= 5) {
    System.out.println(number);
    number++;
}
```

Der sker følgende:

1. `number` starter med værdien `1`.
2. Java undersøger betingelsen `number <= 5`.
3. Hvis betingelsen er `true`, udføres koden i loopet.
4. `number++` øger `number` med 1.
5. Betingelsen undersøges igen.
6. Når `number` bliver `6`, er betingelsen `false`, og loopet stopper.

Det er altså **betingelsen**, der bestemmer, hvor længe loopet fortsætter.

---

### En tæller i et while-loop

Det er almindeligt at bruge en variabel som tæller:

```java
int counter = 0;

while (counter < 3) {
    System.out.println("Hej");
    counter++;
}
```

Output:

```text
Hej
Hej
Hej
```

Variablen `counter` holder styr på, hvor mange gange loopet er blevet udført.

Bemærk især:

```java
counter++;
```

Det svarer til:

```java
counter = counter + 1;
```

Hvis vi glemmer at ændre `counter`, kan loopet fortsætte for evigt.

---

### Uendelige loops

Se dette eksempel:

```java
int number = 1;

while (number <= 5) {
    System.out.println(number);
}
```

Her ændrer `number` sig aldrig.

Betingelsen:

```java
number <= 5
```

vil derfor altid være `true`.

Programmet bliver ved med at skrive:

```text
1
1
1
1
1
...
```

Dette kaldes et **uendeligt loop**.

Når du laver et `while`-loop, er det derfor vigtigt at overveje:

> Hvad skal få loopets betingelse til på et tidspunkt at blive `false`?

---

### Vi kan tælle på andre måder

Et while-loop behøver ikke tælle op med én.

Eksempel:

```java
int number = 2;

while (number <= 10) {
    System.out.println(number);
    number = number + 2;
}
```

Output:

```text
2
4
6
8
10
```

Vi kan også tælle ned:

```java
int number = 5;

while (number > 0) {
    System.out.println(number);
    number--;
}

System.out.println("Start!");
```

Output:

```text
5
4
3
2
1
Start!
```

---

### While-loop med input

Et `while`-loop er særligt nyttigt, når vi **ikke ved på forhånd**, hvor mange gange noget skal gentages.

Eksempel:

```java
Scanner scanner = new Scanner(System.in);

int number = 0;

while (number != 5) {
    System.out.print("Gæt et tal mellem 1 og 10: ");
    number = scanner.nextInt();
}

System.out.println("Du gættede rigtigt!");
```

Her ved vi ikke, hvor mange forsøg brugeren skal bruge.

Loopet fortsætter derfor:

```java
while (number != 5)
```

så længe brugeren **ikke** har skrevet `5`.

---

### Flere betingelser

Betingelsen i et while-loop er en almindelig boolean-betingelse.

Vi kan derfor også bruge eksempelvis `&&`:

```java
int number = 1;

while (number >= 1 && number <= 5) {
    System.out.println(number);
    number++;
}
```

Det vigtigste er, at udtrykket mellem parenteserne kan evalueres til enten:

```text
true
```

eller:

```text
false
```

---

## Do-while

Java har også et loop, der hedder `do-while`.

Det ser sådan ud:

```java
do {
    // kode der skal gentages
} while (betingelse);
```

Eksempel:

```java
int number = 1;

do {
    System.out.println(number);
    number++;
} while (number <= 5);
```

Dette giver samme resultat som vores tidligere eksempel:

```text
1
2
3
4
5
```

### Forskellen på while og do-while

Den vigtigste forskel er, **hvornår betingelsen undersøges**.

Ved `while` undersøges betingelsen **før** koden udføres:

```java
while (betingelse) {
    // kode
}
```

Ved `do-while` udføres koden først, og derefter undersøges betingelsen:

```java
do {
    // kode
} while (betingelse);
```

Det betyder, at koden i et `do-while` altid bliver udført **mindst én gang**.

Eksempel:

```java
int number = 10;

while (number < 5) {
    System.out.println("while");
}
```

Her bliver teksten aldrig skrevet, fordi betingelsen fra starten er `false`.

Men:

```java
int number = 10;

do {
    System.out.println("do-while");
} while (number < 5);
```

Her bliver teksten skrevet én gang.

---

## Kort opsummering

Et `while`-loop bruges til at gentage kode:

```java
while (betingelse) {
    // kode
}
```

Loopet fortsætter, **så længe betingelsen er `true`**.

Et typisk loop består derfor af:

```java
int counter = 0;       // start

while (counter < 5) {  // betingelse
    System.out.println(counter);

    counter++;          // ændring
}
```

Når du læser eller skriver et while-loop, kan du derfor kigge efter tre ting:

1. **Start** – hvilken værdi starter vi med?
2. **Betingelse** – hvornår skal loopet fortsætte?
3. **Ændring** – hvad ændrer sig for hver gennemløb?

Hvis den værdi, som betingelsen afhænger af, aldrig ændrer sig, risikerer du at lave et **uendeligt loop**.  
## Aktiviteter

