# Opgaver – ArrayList - søgning og redigering

I disse opgaver arbejder du videre med søgning, validering, redigering og fjernelse i en `ArrayList`.

Du skal bruge klasser med en `main`-metode og arbejde med en `ArrayList<Book>` i en `Library`-klasse.

Fokus er på:

- at finde et objekt i en liste
- at håndtere `null` og ugyldige værdier
- at sammenligne tekst med `equals()` og `equalsIgnoreCase()`
- at redigere et fundet objekt
- at finde et objekts indeks
- at fjerne et objekt sikkert
- at returnere flere resultater i en ny liste

## Kom i gang

Åbn ugens projekt `uge38-relationer-arraylist`, og opret dagens package
`dag5_arraylist_soegning_redigering`. Klassen hedder det samme som i bogsamlingsprojektet, men det er en ny,
uafhængig udgave i dagens package – rør ikke ved den i `bogsamling` (den afleveres i dag).

Opret klassen `Book`:

```java
public class Book {
    private String title;
    private String author;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public void printInfo() {
        System.out.println(title + " af " + author);
    }
}
```

Opret derefter klassen `Library`:

```java
import java.util.ArrayList;

public class Library {
    private ArrayList<Book> books;

    public Library() {
        books = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }
}
```

Til sidst opretter du en `Main`-klasse med en `main`-metode, hvor du tester dine løsninger.

## Del 1 – Søgning i ArrayList

### Opgave 1 – Find en bog

Implementér metoden nedenfor i `Library`:

```java
public Book findBook(String title) {
    for (Book book : books) {
        if (book.getTitle().equalsIgnoreCase(title)) {
            return book;
        }
    }
    return null;
}
```

Test metoden med:

- en titel, der findes
- en titel, der ikke findes
- en titel skrevet med blandede store og små bogstaver

Skriv derefter kode, der udskriver:

- bogens information, hvis bogen findes
- en passende tekst, hvis den ikke findes

### Opgave 2 – Håndter `null` korrekt

Skab en ny `Library`, tilføj tre bøger, og kald derefter:

```java
Book book = library.findBook("Moby Dick");
```

Besvar:

- Hvad returnerer metoden, når bogen ikke findes?
- Hvilken type kontrol er nødvendig, før du kalder metoder på resultatet?
- Hvorfor kan programmet få en `NullPointerException`, hvis du ikke checker?

Skriv en `if`-sætning, der håndterer begge tilfælde pænt.

### Opgave 3 – Find et indeks

Implementér metoden:

```java
public int findBookIndex(String title) {
    for (int i = 0; i < books.size(); i++) {
        Book book = books.get(i);

        if (book.getTitle().equalsIgnoreCase(title)) {
            return i;
        }
    }
    return -1;
}
```

Test metoden med:

- en eksisterende bog
- en bog, der ikke findes

Hvis metoden returnerer `-1`, skal du forklare, hvad dette betyder.

### Opgave 4 – Søg med flere kriterier

Skriv en metode, der kan finde en bog baseret på både titel og forfatter:

```java
public Book findBook(String title, String author) {
    for (Book book : books) {
        boolean sameTitle = book.getTitle().equalsIgnoreCase(title);
        boolean sameAuthor = book.getAuthor().equalsIgnoreCase(author);

        if (sameTitle && sameAuthor) {
            return book;
        }
    }
    return null;
}
```

Afprøv metoden med:

- en match
- en match, hvor bogstaver er blandet mellem store og små
- en kombination, der ikke findes

Forklar, hvorfor det er nyttigt at bruge `equalsIgnoreCase()` i denne sammenhæng.

## Del 2 – Redigering af objekter

### Opgave 5 – Redigér forfatteren

Implementér en metode i `Library`, der kan ændre forfatteren på en bog:

```java
public boolean updateAuthor(String title, String newAuthor) {
    Book book = findBook(title);

    if (book == null) {
        return false;
    }

    book.setAuthor(newAuthor);
    return true;
}
```

Test metoden med:

- en bog, der findes
- en bog, der ikke findes

Udskriv efterfølgende alle bøger, så du kan se, om ændringen er sket.

### Opgave 6 – Forskellen på `set()` og set-metode

Lav en liste med mindst tre bøger.

Prøv først:

```java
books.set(0, new Book("Dune", "Frank Herbert"));
```

Prøv derefter:

```java
Book book = books.get(0);
book.setAuthor("Frank Herbert");
```

Besvar:

- Hvad gør `ArrayList.set()`?
- Hvad gør `Book.setAuthor()`?
- Hvorfor er det vigtigt at forstå forskellen?
- Hvorfor er det ofte bedre at finde et objekt først og derefter ændre det direkte?

## Del 3 – Fjernelse af objekter

### Opgave 7 – Fjern en bog

Implementér en metode, der fjerner en bog ud fra dens titel:

```java
public boolean removeBook(String title) {
    Book book = findBook(title);

    if (book == null) {
        return false;
    }

    books.remove(book);
    return true;
}
```

Test:

- fjern en bog, der findes
- fjern en bog, der ikke findes
- udskriv listen efter hver fjernelse

Forklar, hvorfor det er vigtigt at kontrollere, om bogen findes, før du fjerner den.

### Opgave 8 – Fjern via indeks

Skriv en metode, der finder indekset for en bog og derefter fjerner den med `remove(index)`:

```java
public boolean removeBookByIndex(String title) {
    int index = findBookIndex(title);

    if (index == -1) {
        return false;
    }

    books.remove(index);
    return true;
}
```

Afprøv metoden og sammenlign den med `removeBook(String title)`.

Besvar:

- Hvornår er det mest praktisk at bruge `remove(book)`?
- Hvornår kan `remove(index)` være mere hensigtsmæssigt?
- Hvad vil der ske, hvis indekset ikke er gyldigt?

## Del 4 – Flere søgeresultater

### Opgave 9 – Find flere bøger af samme forfatter

Implementér metoden:

```java
public ArrayList<Book> findBooksByAuthor(String author) {
    ArrayList<Book> matches = new ArrayList<>();

    for (Book book : books) {
        if (book.getAuthor().equalsIgnoreCase(author)) {
            matches.add(book);
        }
    }

    return matches;
}
```

Test metoden med:

- en forfatter, der har flere bøger
- en forfatter, der ikke findes
- en forfatter med blandede store og små bogstaver

Tænk over:

- Hvad betyder det, at metoden returnerer en tom liste?
- Hvorfor er en tom liste ofte bedre end `null` i en søgning, der kan have flere resultater?

Gennemløb listen med et loop og udskriv hvert resultat.

### Opgave 10 – Søgning med flere match

Tilføj mindst tre bøger, hvor to af dem har samme forfatter.

Kald `findBooksByAuthor()` og vis resultatet.

Besvar:

- Hvor mange bøger bliver fundet?
- Hvorfor er det nyttigt at returnere en liste i stedet for kun ét objekt?

## Del 5 – Edge cases og fejlsikring

### Opgave 11 – Tom liste og ingen match

Lav en ny `Library`, hvor listen er tom.

Test:

- `findBook(...)`
- `findBookIndex(...)`
- `removeBook(...)`
- `findBooksByAuthor(...)`

Besvar:

- Hvad sker der, når listen er tom?
- Hvordan kan du forhindre fejl i programmet?
- Hvilke kontrolstrukturer er nyttige i denne situation?

### Opgave 12 – Flere tests af robusthed

Lav en testsekvens, hvor du prøver følgende:

- søgning giver ingen match
- søgning finder flere matches
- søgning bruger store og små bogstaver
- du forsøger at fjerne en bog, der ikke findes
- du forsøger at redigere en bog, der ikke findes

For hver test skal du skrive en kort kommentar om, hvad programmet gør, og om resultatet er korrekt.

## Del 6 – Videreudvikling

### Opgave 13 – Udvid løsningen

Udvid programmet med mindst én af disse funktioner:

- søg efter en del af en titel med `contains()`
- redigér både titel og forfatter
- undgå at tilføje to bøger med samme titel og forfatter
- vis en tekst, hvis en søgning returnerer en tom liste
- lav en metode, der viser alle bøger i biblioteket

Skriv en kort forklaring på, hvorfor din løsning er nyttig i praksis.

## Opsamling

Når du er færdig, bør du kunne forklare:

- hvordan du finder en bog i en `ArrayList`
- hvordan du kontrollerer, om en søgning fandt noget
- hvordan du redigerer et objekt, der allerede ligger i listen
- hvordan du får indekset for et objekt
- hvordan du fjerner et objekt sikkert
- hvordan du håndterer flere søgeresultater
- forskellen på `null`, `-1` og en tom liste

Det vigtigste princip er:

- søg først
- kontrollér resultatet
- brug objektet kun, hvis det faktisk blev fundet

Dette er grundlaget for sikker og effektiv håndtering af data i en `ArrayList`.
