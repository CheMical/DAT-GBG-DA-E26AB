# Objekter og klasser

## Beskrivelse

I denne lektion arbejder vi videre med egne klasser og objekter. Vi ser på, hvordan objekter kan have forskellige værdier og dermed forskellig tilstand, og hvordan konstruktører kan bruges til at oprette objekter med startværdier.

## Læringsmål

Efter lektionen skal du kunne:

* oprette flere objekter af samme klasse
* forklare, at forskellige objekter har deres egen tilstand
* forklare forskellen på en klasse, en objektvariabel og et objekt
* lave en simpel konstruktør
* bruge en konstruktør til at give et objekt startværdier
* læse og ændre et objekts attributter
* anvende objekter sammen med betingelser og loops

## Se disse videoer før undervisningen

*Videoer indsættes her.*

## Læs nedenstående før undervisningen

### Klassen beskriver – objektet indeholder værdierne

I sidste lektion lavede vi eksempelvis klassen:

```java
public class Person {

    String name;
    int age;
}
```

Klassen beskriver, hvilke egenskaber en person har.

Når vi opretter objekter, får hvert objekt sine egne værdier:

```java
Person person1 = new Person();

person1.name = "Anna";
person1.age = 23;


Person person2 = new Person();

person2.name = "Ali";
person2.age = 31;
```

Objekterne er begge af typen `Person`, men de indeholder forskellige værdier.

Man siger, at objekterne har forskellig **tilstand**.

---

## Referencen og objektet

Se denne linje:

```java
Person person = new Person();
```

Der sker flere ting.

```java
Person
```

er typen.

```java
person
```

er en variabel.

```java
new Person()
```

opretter et nyt objekt.

Variablen `person` giver os adgang til objektet.

Vi kan derfor skrive:

```java
person.name = "Anna";
```

eller:

```java
System.out.println(person.name);
```

---

## En bedre måde at oprette objekter på

Indtil nu har vi skrevet:

```java
Person person = new Person();

person.name = "Anna";
person.age = 23;
```

Det virker, men det ville være praktisk, hvis vi kunne give oplysningerne allerede, når objektet bliver oprettet.

Det kan vi gøre med en **konstruktør**.

```java
public class Person {

    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Nu kan vi skrive:

```java
Person person = new Person("Anna", 23);
```

---

## Hvad betyder `this`?

I konstruktøren står:

```java
this.name = name;
```

Der findes her to forskellige ting med navnet `name`.

```java
this.name
```

er attributten på objektet.

```java
name
```

er den værdi, konstruktøren modtager.

Derfor betyder:

```java
this.name = name;
```

i praksis:

> Gem den modtagne værdi `name` i dette objekts attribut `name`.

Det samme sker her:

```java
this.age = age;
```

---

## Flere objekter

Vi kan nu nemt oprette flere personer:

```java
Person person1 = new Person("Anna", 23);
Person person2 = new Person("Ali", 31);
Person person3 = new Person("Sofie", 19);
```

Alle tre objekter er lavet ud fra samme klasse:

```text
Person
```

men de har forskellig tilstand.

---

## Objekter kan bruges sammen med det, du allerede kender

Objekter erstatter ikke variable, betingelser og loops.

De bruges sammen.

Eksempel:

```java
Person person = new Person("Anna", 23);

if (person.age >= 18) {
    System.out.println(person.name + " er myndig");
}
```

Eller:

```java
Person person1 = new Person("Anna", 23);
Person person2 = new Person("Ali", 31);

if (person1.age > person2.age) {
    System.out.println(person1.name + " er ældst");
} else {
    System.out.println(person2.name + " er ældst");
}
```

På den måde kan vi begynde at samle oplysninger, der hører sammen, i objekter i stedet for at have mange løse variable.

---

## Hvorfor bruger vi klasser?

Uden en klasse kunne oplysninger om personer eksempelvis ligge i separate variable:

```java
String name1 = "Anna";
int age1 = 23;

String name2 = "Ali";
int age2 = 31;
```

Når programmer bliver større, bliver dette hurtigt svært at holde styr på.

Med objekter kan oplysninger, der hører sammen, samles:

```java
Person person1 = new Person("Anna", 23);
Person person2 = new Person("Ali", 31);
```

Det er en af de vigtigste idéer i objektorienteret programmering:

> Data, der beskriver den samme ting, kan samles i et objekt.

## Aktiviteter

I undervisningen arbejder vi videre med egne klasser og opretter flere objekter med forskellige værdier. Vi kombinerer objekter med de variable, betingelser og loops, som vi allerede har arbejdet med.
