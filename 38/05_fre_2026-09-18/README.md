# ArrayList - søgning og redigering

## Beskrivelse

I den forrige lektion arbejdede vi med at oprette og anvende en `ArrayList`. Vi brugte blandt andet `add()`, `get()`, `set()`, `remove()` og `size()`, gennemløb lister med løkker og anvendte en `ArrayList` med objekter fra egne klasser.

I denne lektion arbejder vi videre med at søge efter, redigere og fjerne objekter i en `ArrayList`. Eksemplerne tager udgangspunkt i klasserne `Book` og `Library`.

## Læringsmål

Efter lektionen skal du kunne:

- skrive en metode, der søger efter et objekt ud fra en attribut
- returnere et fundet objekt eller `null`
- kontrollere resultatet af en søgning
- sammenligne tekster med `equals()` og `equalsIgnoreCase()`
- ændre et fundet objekt gennem dets metoder
- forklare forskellen på `ArrayList.set()` og en set-metode på et objekt
- finde et objekts indeks i en liste
- fjerne et objekt sikkert fra en `ArrayList`
- returnere flere søgeresultater i en ny `ArrayList`
- placere søge- og redigeringsfunktionalitet i den klasse, der administrerer listen

## Udgangspunkt

Vi anvender en klasse, som beskriver en bog:

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

Klassen `Library` administrerer en liste af bøger:

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

## Søg efter et objekt

En søgning kan gennemløbe listen og sammenligne titlen på hver bog med den titel, der søges efter:

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

Metoden afsluttes, så snart en bog med den ønskede titel findes. Hvis hele listen gennemløbes uden et match, returneres `null`.

## Brug resultatet af søgningen

Den kaldende kode skal håndtere både et fundet og et ikke-fundet resultat:

```java
Book book = library.findBook("Dune");

if (book != null) {
    book.printInfo();
} else {
    System.out.println("Bogen blev ikke fundet");
}
```

Kontrollen er nødvendig, før der kaldes en metode på resultatet. Ellers kan programmet få en `NullPointerException`.

## Rediger et fundet objekt

Når søgemetoden returnerer et `Book`-objekt, kan objektet ændres gennem dets set-metoder:

```java
Book book = library.findBook("Dune");

if (book != null) {
    book.setAuthor("Frank Herbert");
}
```

Variablen `book` refererer til det samme objekt, som allerede findes i listen. Objektet skal derfor ikke indsættes i listen igen.

Redigeringen kan samles i en metode i `Library`:

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

Returværdien fortæller, om redigeringen lykkedes:

```java
boolean updated = library.updateAuthor("Dune", "Frank Herbert");

if (updated) {
    System.out.println("Bogen blev opdateret");
} else {
    System.out.println("Bogen blev ikke fundet");
}
```

## Forskellen på `set()` og en set-metode

Følgende kode erstatter hele objektet på indeks 0:

```java
books.set(0, new Book("Dune", "Frank Herbert"));
```

Følgende kode beholder objektet, men ændrer dets forfatter:

```java
Book book = books.get(0);
book.setAuthor("Frank Herbert");
```

`ArrayList.set()` erstatter altså et element på en bestemt plads i listen. `Book.setAuthor()` ændrer objektets tilstand.

## Find et indeks

Nogle operationer kræver, at vi kender elementets placering:

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

Returværdien `-1` betyder, at bogen ikke blev fundet.

## Fjern en bog

Et fundet objekt kan fjernes direkte fra listen:

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

En indeksbaseret variant kan skrives sådan:

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

## Søg med flere kriterier

Hvis titlen ikke er tilstrækkelig til at identificere en bog, kan søgningen anvende flere attributter:

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

## Find flere resultater

En søgning kan give flere resultater. I så fald kan metoden returnere en ny liste:

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

Resultatet kan gennemløbes sådan:

```java
ArrayList<Book> matches = library.findBooksByAuthor("Frank Herbert");

for (Book book : matches) {
    book.printInfo();
}
```

Hvis ingen bøger matcher, returnerer metoden en tom liste i stedet for `null`.

## Aktiviteter i undervisningen

### Aktivitet 1: Søg efter en bog

Implementér `findBook(String title)` i `Library`.

Afprøv metoden med:

- en titel, der findes
- en titel, der ikke findes
- samme titel skrevet med andre store og små bogstaver

### Aktivitet 2: Rediger en bog

Implementér en metode, der ændrer forfatteren på en bog. Metoden skal returnere `true`, hvis bogen blev fundet, og ellers `false`.

### Aktivitet 3: Fjern en bog

Implementér en metode, der finder og fjerner en bog ud fra dens titel. Udskriv efterfølgende alle bøger, så resultatet kan kontrolleres.

### Aktivitet 4: Flere resultater

Implementér `findBooksByAuthor(String author)`. Metoden skal returnere alle bøger af den angivne forfatter.

### Aktivitet 5: Videreudvikling

Udvid løsningen med én eller flere af følgende muligheder:

- søg efter en del af en titel med `contains()`
- rediger både titel og forfatter
- undgå at tilføje to bøger med samme titel og forfatter
- vis en besked, hvis en søgning giver en tom liste

## Det vigtigste at tage med

- En søgning efter ét objekt kan returnere objektet eller `null`.
- En søgning efter et indeks kan returnere indekset eller `-1`.
- En søgning efter flere objekter bør returnere en liste, som kan være tom.
- `equals()` og `equalsIgnoreCase()` kan bruges til at sammenligne tekster.
- `ArrayList.set()` erstatter et element i listen.
- En set-metode på objektet ændrer objektets tilstand.
- Et objekt kan findes først og derefter redigeres eller fjernes.
- Søge- og redigeringsmetoder hører naturligt hjemme i den klasse, der administrerer listen.
