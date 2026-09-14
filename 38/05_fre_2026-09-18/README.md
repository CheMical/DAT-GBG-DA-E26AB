# ArrayList - søgning og redigering

## Beskrivelse

I den forrige lektion arbejdede vi med at oprette og anvende en `ArrayList`. Vi brugte blandt andet `add()`, `get()`, `set()`, `remove()` og `size()`, gennemløb lister med løkker og anvendte en `ArrayList` med objekter fra egne klasser.

I denne lektion arbejder vi videre med at søge efter, validere, redigere og fjerne objekter i en `ArrayList`. Fokus er ikke kun at kunne bruge listemetoder, men at kunne administrere en liste af egne objekter på en sikker og fornuftig måde. Eksemplerne tager udgangspunkt i klasserne `Book` og `Library`.

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

Lignende mønstre bruges ofte i programmering:

- søg efter et objekt
- tjek om det blev fundet
- gør noget med objektet, hvis det findes
- vis ellers en passende fejlmeddelelse

## Hvad hvis søgningen ikke finder noget?

Hvis ingen bog matcher, er det vigtigt at håndtere dette tydeligt. Der er flere almindelige eksempler:

```java
Book book = library.findBook("Moby Dick");

if (book == null) {
    System.out.println("Bogen findes ikke i biblioteket");
} else {
    book.printInfo();
}
```

Det samme gælder, hvis listen er tom:

```java
if (books.isEmpty()) {
    System.out.println("Biblioteket er tomt");
}
```

Derfor er den typiske struktur altid:

```java
if (resultat != null) {
    // brug resultatet
} else {
    // vis besked eller håndter fejlen
}
```

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

Det er vigtigt at forstå forskellen:

- `books.set(0, nyBog)` = listen får et nyt objekt på pladsen
- `book.setAuthor(...)` = samme objekt ændres, listen ændres ikke structuralt

Det er derfor, at vi ofte først finder et objekt i listen og derefter ændrer det objekt direkte.

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

Returværdien `-1` betyder, at bogen ikke blev fundet. Det er derfor nyttigt at kunne teste, om indekset er gyldigt, før vi bruger det i `remove()` eller `get()`.

Eksempel:

```java
int index = library.findBookIndex("Dune");

if (index == -1) {
    System.out.println("Bogen findes ikke");
} else {
    System.out.println("Bogen ligger på indeks " + index);
}
```

## Fejlsikring og edge cases

Når vi arbejder med søgning og redigering, skal vi tænke på nogle typiske problemer:

```java
if (books.isEmpty()) {
    System.out.println("Listen er tom");
}

Book book = findBook("Dune");
if (book == null) {
    System.out.println("Ikke fundet");
}

int index = findBookIndex("Dune");
if (index == -1) {
    System.out.println("Indekset findes ikke");
}
```

Det vigtigste er, at vi ikke bruger et resultat, før vi har kontrollert, om det faktisk findes.

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

Når vi fjerner et objekt, er det vigtigt at sikre, at vi kun prøver at fjerne noget, der faktisk findes. Ellers får vi enten en fejlsituation eller en uønsket handling.

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

Det er vigtigt at vide, at en tom liste stadig er en gyldig returværdi. Den betyder ikke “fejl”, men “ikke fundet nogen match”.

## Kobl søgning og redigering til Adventure

Mønstrene fra denne lektion kan senere genbruges i Adventure:

- findItem() kan søge efter et objekt i et rum
- updateItem() kan ændre en ting, f.eks. dens navn eller status
- removeItem() kan fjerne en ting fra inventaret eller rummet
- findItemsByType() kan returnere flere resultater i en liste

På den måde bliver `ArrayList` ikke kun en teknisk struktur, men en måde at organisere spillens data på.

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

### Aktivitet 5: Edge cases og fejlsikring

Test følgende situationer:

- listen er tom
- søgningen giver ingen match
- søgningen finder flere matches
- søgningen bruger store og små bogstaver
- du forsøger at fjerne en bog, der ikke findes

### Aktivitet 6: Videreudvikling

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
- Før vi bruger et resultat, skal vi altid kontrollere, om det faktisk blev fundet.
- Søge- og redigeringsmetoder hører naturligt hjemme i den klasse, der administrerer listen.
