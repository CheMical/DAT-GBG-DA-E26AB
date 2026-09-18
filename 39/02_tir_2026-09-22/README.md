# Design: User stories, Controller, Ansvar og afhængigheder, Coupling og Cohesion

## Beskrivelse

I de foregående lektioner har vi arbejdet med klasser, objekter, metoder og `ArrayList`. Vi har lavet projektet om bogsamling, hvor vi har bygget klasser som `Book` og `Library`, så vi kan oprette bøger, lægge dem i en liste og finde dem igen.

I denne lektion tager vi et nyt skridt: ikke kun at få programmet til at fungere, men at tænke over, hvordan koden er bygget. Et program kan godt køre, men stadig være svært at forstå, ændre og udvide. Derfor arbejder vi med begreber som user stories, controller, ansvar, afhængigheder, coupling og cohesion.

Målet er, at vi lærer at organisere vores kode, så hver klasse har et klart formål, og så flere klasser kan samarbejde uden at blive for tæt koblet sammen.

## Læringsmål

Efter lektionen skal du kunne:

- skrive korte user stories til en funktionalitet
- forklare, hvad en controller gør i et program
- beskrive ansvar i forskellige klasser
- forklare afhængigheder mellem klasser
- forklare forskellen på høj og lav coupling
- forklare forskellen på høj og lav cohesion
- refaktorisere en stor og uoverskuelig klasse til flere mindre klasser

## Se disse videoer før undervisningen:

- Dave Farley: "Managing complexity"
  https://www.youtube.com/watch?v=J8vCm1NdKIc&t=1931s
  Se fra afsnittet "Managing complexity" og frem til slutningen af videoen.

## Læs nedenstående før undervisningen

Før lektionen bør du have genopfrisket:

- klasser og objekter
- metoder og tilstand
- `ArrayList` af egne objekter
- hvordan `Book` og `Library` samarbejder
- forskellen mellem en klasse, der beskriver data, og en klasse, der styrer flowet

Vi bruger bogsamlingen som eksempel, fordi det er det projekt, vi allerede har arbejdet med. Det gør det lettere at se, hvordan designbegreber faktisk hænger sammen med den kode, vi allerede kender.

```java
public class Book {
    private String title;
    private String author;
    private boolean read;

    public Book(String title, String author) {
        this.title = title;
        this.author = author;
        this.read = false;
    }

    public String getTitle() {
        return title;
    }

    public boolean isRead() {
        return read;
    }

    public void markAsRead() {
        read = true;
    }
}
```

```java
public class Library {
    private ArrayList<Book> books;

    public Library() {
        books = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
    }

    public Book findBookByTitle(String title) {
        for (Book book : books) {
            if (book.getTitle().equalsIgnoreCase(title)) {
                return book;
            }
        }
        return null;
    }
}
```

## Aktiviteter i undervisningen

### 1. User stories i bogsamling

En user story er en kort beskrivelse af en funktionalitet fra brugerens synspunkt. Den beskriver ikke, hvordan vi skal bygge løsningen, men hvad brugeren vil kunne gøre.

Eksempler til bogsamlingen:

- Som bruger vil jeg kunne tilføje en bog, så jeg kan samle mine bøger.
- Som bruger vil jeg kunne finde en bog ud fra titel, så jeg hurtigt kan finde den igen.
- Som bruger vil jeg kunne markere en bog som læst, så jeg kan holde styr på mine læste bøger.
- Som bruger vil jeg kunne se alle bøger i min samling, så jeg kan få et overblik.

User stories hjælper os med at fokusere på den funktionalitet, programmet faktisk skal kunne.

Diskussion:

- Hvilke user stories passer godt til projektet bogsamling?
- Hvad er vigtigt at tænke over, før vi begynder at kode?
- Hvorfor er det nyttigt at skrive user stories, før vi designet klasserne?

### 2. Controller

En controller er ofte den del af programmet, der styrer flowet. Den læser input, vælger den rigtige handling og kalder de rette metoder i andre klasser.

Et simpelt eksempel kunne være en `LibraryController`, der styrer menuen i konsolprogrammet:

```java
public class LibraryController {
    private Library library;
    private Scanner scanner;

    public LibraryController(Library library, Scanner scanner) {
        this.library = library;
        this.scanner = scanner;
    }

    public void start() {
        System.out.println("1. Tilføj bog");
        System.out.println("2. Find bog");
        System.out.println("3. Vis alle bøger");

        String input = scanner.nextLine();
        // fortolk input og kald passende metode
    }
}
```

Controlleren gør ikke alt selv. Den styrer ikke bogens data direkte. Det er `Book` og `Library`, der holder informationen og udfører de konkrete handlinger.

Det er vigtigt, at controlleren ikke bliver en "stor bunke af alt". Den skal styre flowet, ikke tage over for hele programlogikken.

### 3. Ansvar og afhængigheder

Når vi designer klasser, er det vigtigt at spørge:

- Hvad er klassen ansvarlig for?
- Hvilken information skal den kende til?
- Hvilke metoder hører naturligt til klassen?
- Hvilke andre klasser bruger den?

Eksempler i bogsamlingen:

- `Book` har ansvar for beskrivelser af en bog: titel, forfatter, læsestatus
- `Library` har ansvar for at holde en samling af bøger og finde/fjerne/opdatere dem
- `LibraryController` har ansvar for menuen og brugerinput
- `Main` har ansvar for at starte programmet og lave testkald

Hvis en klasse har for mange ansvar, bliver den svær at forstå og svær at ændre. Derfor er det vigtigt, at klasserne har tydelige roller.

Afhængigheder handler om, at klasser bruger hinanden. Det er normalt okay, men vi vil gerne holde afhængighederne lavt koblede, så en ændring ikke påvirker for mange andre klasser.

### 4. Coupling

Coupling betyder, hvor tæt klasser er koblet sammen.

- Lav coupling = klasserne er relativt uafhængige af hinanden
- Høj coupling = klasserne er meget afhængige af hinanden

Eksempel på høj coupling:

```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Book> books = new ArrayList<>();

        Book book = new Book("Dune", "Frank Herbert");
        books.add(book);

        // meget kode her: søgning, udskrift, validation, logging, menu
    }
}
```

Her bliver `Main` ansvarlig for for mange ting. Koden bliver svær at læse, og tingene står meget tæt sammen.

Eksempel på lavere coupling:

```java
public class Main {
    public static void main(String[] args) {
        Library library = new Library();
        LibraryController controller = new LibraryController(library, new Scanner(System.in));
        controller.start();
    }
}
```

Nu er `Main` kun ansvarlig for at starte programmet. De konkrete handlinger ligger i passende klasser.

### 5. Cohesion

Cohesion handler om, hvor godt metoderne i en klasse arbejder sammen mod samme formål.

- Høj cohesion = klassen har et tydeligt formål
- Lav cohesion = klassen blandes med mange forskellige emner

Eksempel på lav cohesion:

```java
public class Library {
    public void addBook(Book book) { ... }
    public void printMenu() { ... }
    public void readInput() { ... }
    public void saveToFile() { ... }
    public void findBookByTitle(String title) { ... }
}
```

Her blandes flere forskellige ting i samme klasse.

Eksempel på høj cohesion:

```java
public class Library {
    public void addBook(Book book) { ... }
    public void findBookByTitle(String title) { ... }
    public void removeBook(String title) { ... }
    public void printBooks() { ... }
}
```

Her hører metoderne sammen: de arbejder alle med bibliotekets samling af bøger.

### 6. Refaktoring i bogsamlingen

Et godt design bliver tydeligt, når vi refaktorerer.

Hvis vi starter med at have alt i `Main`, kan vi løbe ind i dette problem:

- opret bøger
- tilføj bøger til listen
- søg efter en bog
- vis alle bøger
- læs brugerinput
- vis menuer
- håndter valg

Det er meget, meget meget i én klasse.

I stedet kan vi dele det op:

- `Book` beskriver en bog
- `Library` administrerer listen
- `LibraryController` styrer brugerinteraktionen
- `Main` starter programmet

På den måde bliver koden mere overskuelig og lettere at udvikle videre.

### 7. Opgaver i undervisningen

1. Skriv 3–5 user stories til projektet bogsamling.
2. Beskriv, hvilket ansvar hver af følgende klasser bør have: `Book`, `Library`, `LibraryController`, `Main`.
3. Tag et eksempel på kode, hvor meget står i `Main`, og diskuter, hvordan det kan refaktoreres.
4. Forklar, hvor der er høj coupling eller lav cohesion i et eksempel.
5. Skriv en kort beskrivelse af, hvordan en bedre designløsning ville se ud i bogsamlingen.

### 8. Opsamling

Design handler ikke kun om, hvordan koden ser ud, men om, hvordan den er organiseret. Når vi arbejder med user stories, controller, ansvar, afhængigheder, coupling og cohesion, så skaber vi kode, der er:

- lettere at læse
- lettere at ændre
- lettere at udvide
- mere robust i større programmer

Det er et vigtigt næste skridt i vores objektorienterede programmering, fordi det går fra at have kode, der virker, til at have kode, der er godt designet.

Det betyder også, at vi bliver bedre til at løse problemer, ikke kun at skrive funktioner. Vi lærer at tænke som udviklere, der planlægger og strukturerer et system, før det bliver for komplekst.
