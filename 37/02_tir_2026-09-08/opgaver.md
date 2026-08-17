# Opgaver – Objekter og klasser

I disse opgaver arbejder du videre med egne klasser og objekter.

Fokus er på:

* konstruktører
* `this`
* `private` og `public`
* getters og setters
* dataindkapsling
* validering af data

---

# Del 1 – Konstruktører

## Opgave 1 – Person med konstruktør

Mandag lavede du en klasse `Person`, hvor værdierne blev sat efter objektet var oprettet:

```java
Person person = new Person();

person.name = "Anna";
person.age = 23;
```

Nu skal du ændre klassen, så navn og alder gives, når objektet bliver oprettet.

Klassen skal have en konstruktør:

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

Opret derefter to personer i `Main`:

```java
Person person1 = new Person("Anna", 23);
Person person2 = new Person("Ali", 31);
```

Udskriv oplysninger om begge personer.

### Tænk over

Hvad betyder følgende?

```java
this.name = name;
```

Prøv at forklare forskellen på:

```text
this.name
```

og:

```text
name
```

---

## Opgave 2 – Book med konstruktør

Opret klassen:

```text
Book
```

Den skal have følgende attributter:

```java
String title;
String author;
int numberOfPages;
```

Lav en konstruktør, som modtager alle tre værdier.

Du skal kunne oprette en bog sådan:

```java
Book book = new Book("The Hobbit", "J.R.R. Tolkien", 310);
```

Opret mindst tre bøger og udskriv deres oplysninger.

Find derefter den bog, der har flest sider.

---

# Del 2 – `private` og `public`

## Opgave 3 – Gør Person-attributterne private

Ændr din `Person`-klasse, så attributterne bliver `private`:

```java
public class Person {

    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Prøv nu følgende i `Main`:

```java
Person person = new Person("Anna", 23);

System.out.println(person.name);
```

Hvad sker der?

Læs fejlmeddelelsen i IntelliJ.

### Spørgsmål

1. Hvorfor kan `Main` ikke længere tilgå `name`?
2. Kan `Person`-klassen selv stadig tilgå `name`?
3. Hvad er forskellen på `private` og `public`?

---

## Opgave 4 – Tilføj getters

Tilføj følgende metoder til `Person`:

```java
public String getName() {
    return name;
}

public int getAge() {
    return age;
}
```

Du skal nu kunne skrive:

```java
Person person = new Person("Anna", 23);

System.out.println(person.getName());
System.out.println(person.getAge());
```

Udskriv:

```text
Anna er 23 år
```

uden at tilgå attributterne direkte.

---

# Del 3 – Ændring af objekters tilstand

## Opgave 5 – Setter til alder

Tilføj en metode til `Person`, så alderen kan ændres:

```java
public void setAge(int age) {
    this.age = age;
}
```

Afprøv:

```java
Person person = new Person("Anna", 23);

person.setAge(24);

System.out.println(person.getAge());
```

Prøv derefter:

```java
person.setAge(-100);
```

Hvad sker der?

Er `-100` en fornuftig alder?

---

# Del 4 – Dataindkapsling og validering

## Opgave 6 – En alder skal være gyldig

I den forrige opgave kunne vi skrive:

```java
person.setAge(-100);
```

Det betyder, at objektet kan ende med at indeholde ugyldige data.

Ændr `setAge()`, så alderen kun ændres, hvis den er mellem `0` og `130`.

Eksempel:

```java
public void setAge(int age) {

    if (age >= 0 && age <= 130) {
        this.age = age;
    }
}
```

Afprøv følgende:

```java
Person person = new Person("Anna", 23);

person.setAge(40);
System.out.println(person.getAge());

person.setAge(-5);
System.out.println(person.getAge());

person.setAge(200);
System.out.println(person.getAge());
```

### Tænk over

Hvis `age` i stedet havde været:

```java
public int age;
```

kunne en anden klasse skrive:

```java
person.age = -500;
```

Ved at gøre attributten:

```java
private int age;
```

og kun ændre den gennem:

```java
setAge(...)
```

kan klassen kontrollere, hvilke værdier der accepteres.

Det er et eksempel på **dataindkapsling**.

---

## Opgave 7 – BankAccount

Nu skal du lave en klasse, hvor fordelene ved dataindkapsling bliver endnu tydeligere.

Opret klassen:

```text
BankAccount
```

med:

```java
private String owner;
private double balance;
```

Lav en konstruktør:

```java
public BankAccount(String owner, double balance) {
    this.owner = owner;
    this.balance = balance;
}
```

Lav også:

```java
public String getOwner() {
    return owner;
}

public double getBalance() {
    return balance;
}
```

### Indbetaling

Lav metoden:

```java
public void deposit(double amount) {

    if (amount > 0) {
        balance = balance + amount;
    }
}
```

Afprøv:

```java
BankAccount account = new BankAccount("Anna", 1000);

account.deposit(500);

System.out.println(account.getBalance());
```

Resultatet skal være:

```text
1500.0
```

### Prøv ugyldige data

Prøv:

```java
account.deposit(-500);
```

Saldoen skal ikke ændres.

### Spørgsmål

Hvorfor er dette bedre end at have:

```java
public double balance;
```

?

Hvis `balance` var `public`, kunne enhver del af programmet skrive:

```java
account.balance = -1000000;
```

Når attributten er `private`, kan klassen selv bestemme, hvordan saldoen må ændres.

---

## Opgave 8 – Hæv penge

Tilføj metoden:

```java
public void withdraw(double amount)
```

Der må kun hæves penge, hvis:

* beløbet er større end `0`
* der er penge nok på kontoen

Eksempel:

```java
BankAccount account = new BankAccount("Anna", 1000);

account.withdraw(300);
```

Saldo:

```text
700.0
```

Men:

```java
account.withdraw(1000);
```

må ikke ændre saldoen.

### Ekstra

Udskriv en besked, hvis hævningen ikke kan gennemføres:

```text
Der er ikke penge nok på kontoen
```

---

# Del 5 – Validering i konstruktøren

## Opgave 9 – Product

Opret klassen:

```text
Product
```

med:

```java
private String name;
private double price;
```

Et produkt må ikke have en negativ pris.

Lav derfor en konstruktør, der kontrollerer værdien.

Et simpelt eksempel kan være:

```java
public Product(String name, double price) {

    this.name = name;

    if (price >= 0) {
        this.price = price;
    }
}
```

Lav getters til begge attributter.

Afprøv:

```java
Product product1 = new Product("Kaffe", 49.95);
Product product2 = new Product("Te", -20);
```

Undersøg værdien af `price` på begge objekter.

### Overvej

Er `0` en god standardværdi, hvis der gives en ugyldig pris?

Hvordan kunne programmet ellers reagere?

Du behøver ikke løse dette endnu.

---

## Opgave 10 – Temperature

Opret klassen:

```text
Temperature
```

med:

```java
private double degrees;
```

Temperaturen må ikke være lavere end cirka:

```text
-273.15 °C
```

Lav:

```java
public void setDegrees(double degrees)
```

så værdien kun ændres, hvis den er mindst `-273.15`.

Lav også:

```java
public double getDegrees()
```

Afprøv eksempelvis:

```java
Temperature temperature = new Temperature();

temperature.setDegrees(20);
System.out.println(temperature.getDegrees());

temperature.setDegrees(-300);
System.out.println(temperature.getDegrees());
```

---

# Del 6 – Metoder der beskriver adfærd

## Opgave 11 – Person kan have fødselsdag

Tilføj følgende metode til `Person`:

```java
public void birthday() {
    age++;
}
```

Afprøv:

```java
Person person = new Person("Anna", 23);

person.birthday();

System.out.println(person.getAge());
```

Resultatet skal være:

```text
24
```

### Tænk over

Sammenlign:

```java
person.setAge(24);
```

med:

```java
person.birthday();
```

Hvilken af metoderne fortæller tydeligst, **hvad der sker**?

---

## Opgave 12 – BankAccount uden `setBalance`

Se på klassen `BankAccount`.

Du har metoderne:

```java
deposit(...)
withdraw(...)
getBalance()
```

Men du har ikke:

```java
setBalance(...)
```

Diskutér med en medstuderende:

1. Hvorfor kunne det være en fordel?
2. Skal alle `private` attributter nødvendigvis have en setter?
3. Hvilken forskel er der på:

```java
account.setBalance(500);
```

og:

```java
account.deposit(500);
```

---

# Del 7 – Lidt sværere

## Opgave 13 – Student

Opret klassen:

```text
Student
```

med:

```java
private String name;
private int semester;
```

Et semester skal være mellem `1` og `7`.

Lav:

* konstruktør
* `getName()`
* `getSemester()`
* `setSemester()`

`setSemester()` må kun acceptere værdier fra `1` til `7`.

Afprøv både gyldige og ugyldige værdier.

---

## Opgave 14 – Speedometer

Opret klassen:

```text
Car
```

med:

```java
private String model;
private int speed;
```

Når en bil oprettes, skal hastigheden være `0`.

Lav metoden:

```java
public void accelerate()
```

som øger hastigheden med `10`.

Lav også:

```java
public void brake()
```

som reducerer hastigheden med `10`.

Hastigheden må aldrig blive negativ.

Eksempel:

```java
Car car = new Car("Toyota");

car.accelerate();
car.accelerate();

System.out.println(car.getSpeed());
```

skal give:

```text
20
```

Men hvis:

```java
car.brake();
car.brake();
car.brake();
```

kaldes, må hastigheden ikke ende på:

```text
-10
```

---

# Udfordring – Design din egen klasse

Lav selv en klasse, der repræsenterer noget fra virkeligheden.

Det kunne eksempelvis være:

* `Movie`
* `Game`
* `Employee`
* `HotelRoom`
* `Bike`
* `CoffeeMachine`

Klassen skal have:

* mindst tre `private` attributter
* en konstruktør
* mindst to getters
* mindst én metode, der ændrer objektets tilstand
* mindst én validering, der forhindrer ugyldige værdier

Opret mindst to objekter af klassen og afprøv dem fra `Main`.

---

# Opsamling

Når du er færdig, skal du kunne forklare følgende klasse:

```java
public class BankAccount {

    private String owner;
    private double balance;

    public BankAccount(String owner, double balance) {
        this.owner = owner;
        this.balance = balance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {

        if (amount > 0) {
            balance = balance + amount;
        }
    }
}
```

Du skal kunne forklare ordene:

* klasse
* objekt
* attribut
* konstruktør
* `this`
* `private`
* `public`
* getter
* dataindkapsling
* validering

