# Variable, datatyper og aritmetiske operatorer

## Beskrivelse

## Forberedelse
Se disse videoer:  
[Variables](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=10m58s) (til: 00:31:30)  
[Aritmetiske operatorer](https://www.youtube.com/watch?v=xTtL8E4LzTQ&list=PLEeqf0uSZqXsz7oU2U-VAxhQZ021PRVnd&t=54m8s) (til: 01:02:29 )  


## Læringsmål
- primitive datatyper i Java
- Strings 

## Indhold

I dette afsnit skal du arbejde med **variable og datatyper i Java**.

En variabel kan betragtes som en lille navngivet plads i computerens hukommelse, hvor vi kan gemme en værdi.

For eksempel:

```java
int age = 25;
```

Her sker der tre ting:

* `int` angiver hvilken **datatype** variablen har
* `age` er variablens **navn**
* `25` er den **værdi**, der gemmes i variablen

Vi kan efterfølgende bruge variablen:

```java
System.out.println(age);
```

Output:

```text
25
```

---

### Variable kan ændre værdi

Navnet *variabel* kommer af, at værdien kan variere.

```java
int age = 25;

System.out.println(age);

age = 26;

System.out.println(age);
```

Output:

```text
25
26
```

Når variablen allerede er oprettet, skriver vi ikke datatypen igen:

```java
int age = 25;

age = 26;
```

Ikke:

```java
int age = 25;

int age = 26;   // fejl
```

---

## Datatyper

Java skal vide, hvilken slags data en variabel skal indeholde.

Nogle af de mest almindelige datatyper er:

| Datatype  | Bruges til | Eksempel  |
| --------- | ---------- | --------- |
| `int`     | hele tal   | `42`      |
| `double`  | decimaltal | `12.5`    |
| `boolean` | sand/falsk | `true`    |
| `char`    | ét tegn    | `'A'`     |
| `String`  | tekst      | `"Hello"` |

Vi ser nærmere på dem nedenfor.

---

## `int` – hele tal

Datatypen `int` bruges til hele tal.

```java
int age = 23;
int numberOfStudents = 28;
int temperature = -4;
```

En `int` kan både være positiv, negativ eller nul.

```java
int a = 10;
int b = -5;
int c = 0;
```

Vi kan også regne med variable:

```java
int price = 20;
int number = 3;

int totalPrice = price * number;

System.out.println(totalPrice);
```

Output:

```text
60
```

### Prøv selv

Hvad tror du bliver skrevet ud?

```java
int x = 10;
int y = 4;

int result = x + y;

System.out.println(result);
```

Prøv derefter at ændre `+` til:

```text
-
*
/
```

---

## `double` – decimaltal

Hvis vi vil arbejde med tal med decimaler, kan vi bruge `double`.

```java
double height = 1.82;
double price = 19.95;
double temperature = 21.5;
```

Bemærk, at Java bruger **punktum** som decimaltegn:

```java
double price = 19.95;
```

og ikke:

```java
double price = 19,95;
```

Vi kan også regne med `double`:

```java
double price = 12.50;
int number = 4;

double totalPrice = price * number;

System.out.println(totalPrice);
```

Output:

```text
50.0
```

---
## Flere datatyper til tal: `long` og `float`

Indtil videre har vi brugt:

```java
int age = 25;
double price = 19.95;
```

I de fleste almindelige Java-programmer er:

* `int` et godt standardvalg til **hele tal**
* `double` et godt standardvalg til **decimaltal**

Java har dog også andre numeriske datatyper. To af dem er `long` og `float`.

---

## `long` – meget store hele tal

En `int` kan kun indeholde tal inden for et bestemt interval.

Den største værdi, en `int` kan indeholde, er cirka **2,1 milliarder**.

Hvis vi skal arbejde med større hele tal, kan vi bruge `long`.

```java
long population = 8_100_000_000L;
```

Bemærk `L` efter tallet:

```java
8100000000L
```

Det fortæller Java, at tallet skal behandles som en `long`.

Underscores `_` kan bruges til at gøre store tal lettere at læse:

```java
long population = 8_100_000_000L;
```

Det svarer til:

```java
long population = 8100000000L;
```

### Hvornår bruger man `long`?

Brug typisk `long`, når du ved, at et helt tal kan blive større end det, en `int` kan indeholde.

Eksempler kunne være:

```java
long numberOfViews = 5_600_000_000L;
long distanceInMeters = 12_000_000_000L;
```

Til almindelige mindre hele tal bruger vi normalt stadig `int`:

```java
int age = 25;
int numberOfStudents = 30;
int numberOfBooks = 120;
```

---

## `float` – decimaltal med mindre præcision

Java har også datatypen `float` til decimaltal.

Eksempel:

```java
float temperature = 21.5F;
```

Bemærk `F` efter tallet.

Uden `F` opfatter Java normalt et decimaltal som en `double`.

Derfor virker dette:

```java
double temperature = 21.5;
```

mens en `float` typisk skrives:

```java
float temperature = 21.5F;
```

---

## `float` eller `double`?

Både `float` og `double` kan gemme decimaltal.

Forskellen er især, hvor præcist tallet kan gemmes.

`double` har større præcision end `float`.

For eksempel:

```java
float number1 = 1.23456789F;
double number2 = 1.23456789;

System.out.println(number1);
System.out.println(number2);
```

Du vil kunne opleve, at `float` ikke kan bevare lige så mange decimaler præcist som `double`.

Derfor bruger vi normalt:

```java
double
```

til decimaltal i vores programmer.

Brug kun `float`, hvis der er en særlig grund til det.

---

## Hvilken datatype skal jeg vælge?

Som udgangspunkt kan du bruge denne tommelfingerregel:

| Jeg vil gemme...                                      | Typisk datatype |
| ----------------------------------------------------- | --------------- |
| Et almindeligt helt tal                               | `int`           |
| Et meget stort helt tal                               | `long`          |
| Et decimaltal                                         | `double`        |
| Et decimaltal, hvor mindre præcision er tilstrækkelig | `float`         |

Eksempler:

```java
int age = 24;

long numberOfViews = 4_500_000_000L;

double height = 1.82;

float temperature = 21.5F;
```

På dette kursus vil du i langt de fleste tilfælde kunne bruge **`int` til hele tal og `double` til decimaltal**.

Det vigtigste er derfor ikke at kunne huske alle datatyper udenad, men at forstå, at valget af datatype afhænger af, **hvilken slags værdi vi vil gemme**.

---

## Heltalsdivision

Der er en vigtig forskel på `int` og `double`.

Se dette eksempel:

```java
int result = 5 / 2;

System.out.println(result);
```

Hvad tror du resultatet bliver?

Det bliver:

```text
2
```

Begge tal er hele tal, og derfor foretager Java **heltalsdivision**.

Decimaldelen bliver fjernet.

Hvis vi i stedet skriver:

```java
double result = 5.0 / 2.0;

System.out.println(result);
```

bliver resultatet:

```text
2.5
```

---

## `boolean` – sand eller falsk

En `boolean` kan kun indeholde én af to værdier:

```java
true
```

eller:

```java
false
```

Eksempel:

```java
boolean isStudent = true;
boolean hasDriversLicense = false;
```

Boolean-værdier bruges meget, når programmer senere skal træffe beslutninger.

For eksempel:

```java
int age = 20;

boolean isAdult = age >= 18;

System.out.println(isAdult);
```

Output:

```text
true
```

Udtrykket:

```java
age >= 18
```

er enten sandt eller falsk.

---

## `char` – ét tegn

Datatypen `char` bruges til **ét enkelt tegn**.

```java
char grade = 'A';
char letter = 'K';
char symbol = '?';
```

Et `char` skrives med **enkelt citationstegn**:

```java
'A'
```

---

## `String` – tekst

Når vi vil gemme tekst, bruger vi `String`.

```java
String name = "Anna";
String city = "København";
String message = "Hello world";
```

En `String` skrives med **dobbelte citationstegn**:

```java
"Hello"
```

Vi kan skrive en variabel ud:

```java
String name = "Anna";

System.out.println(name);
```

Output:

```text
Anna
```

Vi kan også kombinere tekst og variable:

```java
String name = "Anna";
int age = 22;

System.out.println("Hej " + name);
System.out.println("Du er " + age + " år gammel");
```

Output:

```text
Hej Anna
Du er 22 år gammel
```

Operatoren `+` bruges her til at sætte tekst sammen.

---

## `char` eller `String`?

Bemærk forskellen:

```java
char letter = 'A';
```

og:

```java
String letter = "A";
```

Begge indeholder umiddelbart bogstavet A, men de har forskellige datatyper.

`char` indeholder **ét tegn**, mens `String` bruges til **tekst**.

```java
char firstLetter = 'M';

String firstName = "Mads";
```

---

## Deklaration og tildeling

Når vi skriver:

```java
int age = 25;
```

foretager vi både en **deklaration** og en **tildeling**.

Vi kan også gøre det i to trin.

Først deklarerer vi variablen:

```java
int age;
```

Derefter tildeler vi den en værdi:

```java
age = 25;
```

Det svarer altså til:

```java
int age = 25;
```

---

## Variable skal have den rigtige datatype

Java kontrollerer, at værdien passer til variablens datatype.

Dette er gyldigt:

```java
int age = 25;
```

Dette er ikke gyldigt:

```java
int age = "25";
```

`"25"` er nemlig tekst og ikke et helt tal.

På samme måde er dette forkert:

```java
boolean isStudent = "true";
```

mens dette er korrekt:

```java
boolean isStudent = true;
```

Bemærk forskellen på:

```java
true
```

og:

```java
"true"
```

Den første er en `boolean`.

Den anden er en `String`.

---

## Giv dine variable gode navne

Variable bør have navne, der fortæller, hvad de indeholder.

Undgå eksempelvis:

```java
int x = 25;
String s = "Peter";
double d = 199.95;
```

Skriv hellere:

```java
int age = 25;
String name = "Peter";
double price = 199.95;
```

Det gør programmet meget lettere at læse.

I Java skriver man normalt variabelnavne med **camelCase**:

```java
int numberOfStudents = 25;
double averageTemperature = 18.5;
boolean hasDriversLicense = true;
```

Det første ord starter med lille bogstav. De efterfølgende ord starter med stort bogstav.

---

## Variable kan beregnes ud fra andre variable

En variabel behøver ikke få en fast værdi.

Den kan også få sin værdi fra en beregning:

```java
int width = 10;
int height = 5;

int area = width * height;

System.out.println(area);
```

Output:

```text
50
```

Et andet eksempel:

```java
double price = 100.0;
double discount = 20.0;

double finalPrice = price - discount;

System.out.println(finalPrice);
```

---

## Et samlet eksempel

Her er et lille program, der bruger flere forskellige datatyper:

```java
public class Main {

    public static void main(String[] args) {

        String name = "Amalie";
        int age = 21;
        double height = 1.72;
        boolean isStudent = true;
        char classLetter = 'A';

        System.out.println("Navn: " + name);
        System.out.println("Alder: " + age);
        System.out.println("Højde: " + height);
        System.out.println("Studerende: " + isStudent);
        System.out.println("Hold: " + classLetter);
    }
}
```

Output:

```text
Navn: Amalie
Alder: 21
Højde: 1.72
Studerende: true
Hold: A
```

---

## Prøv selv

Lav et lille Java-program med variable, der beskriver dig selv.

Opret eksempelvis variable til:

* dit navn
* din alder
* din højde
* om du er studerende
* dit første bogstav

Eksempel:

```java
String name = "Sofie";
int age = 23;
double height = 1.68;
boolean isStudent = true;
char firstLetter = 'S';
```

Skriv derefter værdierne ud med:

```java
System.out.println(...);
```

---

## Kan du forudsige resultatet?

Prøv først at finde svaret **uden at køre programmerne**.

### Eksempel 1

```java
int a = 4;
int b = 3;

int result = a + b * 2;

System.out.println(result);
```

Hvad bliver skrevet ud?

### Eksempel 2

```java
int number = 10;

number = number + 5;

System.out.println(number);
```

Hvad bliver skrevet ud?

### Eksempel 3

```java
String firstName = "Ada";
String lastName = "Lovelace";

System.out.println(firstName + " " + lastName);
```

Hvad bliver skrevet ud?

### Eksempel 4

```java
int x = 5;
int y = 2;

System.out.println(x / y);
```

Hvad bliver skrevet ud?

---

## Det vigtigste at tage med

Efter denne forberedelse skal du især være fortrolig med:

* hvad en **variabel** er
* hvordan en variabel **deklareres**
* hvordan en variabel får **tildelt en værdi**
* forskellen på `int`, `double`, `boolean`, `char` og `String`
* at Java kontrollerer, om værdien passer til datatypen
* at værdien i en variabel kan ændres
* at variable kan bruges i beregninger
* at gode variabelnavne gør programmer lettere at forstå

Du behøver ikke kunne huske alle detaljer udenad. Det vigtigste er, at du kan **læse de små kodeeksempler og eksperimentere med dem**.


## Aktiviteter
