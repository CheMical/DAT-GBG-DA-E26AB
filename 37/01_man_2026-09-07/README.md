# Objekter og klasser

## Beskrivelse

I denne lektion introduceres klasser og objekter. Vi ser først på klasser, som du allerede har anvendt i Java, og derefter laver vi vores første egne klasser og objekter.

## Læringsmål

Efter lektionen skal du kunne:

* forklare forskellen på en **klasse** og et **objekt**
* oprette og anvende objekter fra eksisterende Java-klasser
* genkende brug af klasser og objekter i kode, du allerede kender
* oprette en simpel klasse med attributter
* oprette objekter af din egen klasse
* tilgå og ændre et objekts attributter

## Se disse videoer før undervisningen

[random numbers](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=1h22m28s) (til: 01:27:28) 
[While loops, number guessing game](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=1h27m28s) (til: 01:42:37) 


## Læs nedenstående før undervisningen

### Fra datatyper til objekter

Indtil nu har du blandt andet arbejdet med primitive datatyper:

```java
int age = 25;
double price = 19.95;
boolean active = true;
```

Men Java-programmer består ikke kun af simple værdier.

Vi har faktisk allerede arbejdet med **objekter**.

Et eksempel er `Scanner`:

```java
Scanner scanner = new Scanner(System.in);
```

Her er:

* `Scanner` en **klasse**
* `scanner` en variabel, som refererer til et **objekt**
* `new Scanner(System.in)` opretter objektet

Man kan tænke på en klasse som en **opskrift eller skabelon**, mens et objekt er en konkret ting, der er lavet ud fra skabelonen.

---

### Klasser, som Java allerede indeholder

Java indeholder mange klasser, som vi kan bruge direkte.

#### Random

Klassen `Random` kan bruges til at generere tilfældige tal.

```java
import java.util.Random;

Random random = new Random();

int number = random.nextInt(10);

System.out.println(number);
```

Her opretter vi først et `Random`-objekt:

```java
Random random = new Random();
```

Derefter bruger vi objektets metode:

```java
random.nextInt(10);
```

---

### Objekter har funktionalitet

Et objekt kan have funktionalitet, som vi kan anvende gennem metoder.

Det har du allerede gjort med `Scanner`:

```java
Scanner scanner = new Scanner(System.in);

String name = scanner.nextLine();
int age = scanner.nextInt();
```

Her kalder vi metoderne:

```text
scanner.nextLine()
scanner.nextInt()
```

på objektet `scanner`.

Den generelle form er:

```text
objekt.metode()
```

---

### Math er lidt anderledes

Du har måske også set:

```java
double result = Math.sqrt(25);
```

eller:

```java
int largest = Math.max(10, 20);
```

Her opretter vi ikke først et objekt:

```java
Math math = new Math();
```

I stedet bruger vi metoder direkte på klassen `Math`.

Det skyldes, at metoder som `sqrt()` og `max()` er **static**.

Du behøver ikke kunne forklare `static` i detaljer endnu. Det vigtige er blot at lægge mærke til forskellen:

```java
random.nextInt(10);
```

kaldes på et **objekt**, mens:

```java
Math.sqrt(25);
```

kaldes direkte på en **klasse**.

---

## Vores egen klasse

Vi kan også selv lave klasser.

Forestil dig, at vores program skal arbejde med personer.

Vi kan lave klassen:

```java
public class Person {

    String name;
    int age;
}
```

Klassen beskriver, hvilke oplysninger en `Person` har.

I dette tilfælde:

* et navn
* en alder

Disse kaldes klassens **attributter** eller **felter**.

---

## Opret et objekt

I `Main` kan vi oprette en person:

```java
public class Main {

    public static void main(String[] args) {

        Person person = new Person();

        person.name = "Anna";
        person.age = 23;

        System.out.println(person.name);
        System.out.println(person.age);
    }
}
```

Linjen:

```java
Person person = new Person();
```

opretter et nyt objekt af klassen `Person`.

Vi kan derefter arbejde med objektets attributter:

```java
person.name
person.age
```

---

## Flere objekter af samme klasse

En klasse kan bruges til at oprette mange objekter.

```java
Person person1 = new Person();

person1.name = "Anna";
person1.age = 23;


Person person2 = new Person();

person2.name = "Mohammed";
person2.age = 27;
```

`person1` og `person2` er to forskellige objekter, men begge er lavet ud fra klassen `Person`.

Man kan derfor tænke på:

```text
Person
```

som en type på samme måde som:

```text
int
double
boolean
String
```

Forskellen er, at `Person` er en type, vi selv har lavet.

## Aktiviteter

I undervisningen arbejder vi videre med klasser og objekter og laver en række små programmer, hvor vi både anvender eksisterende Java-klasser og vores egne klasser.
