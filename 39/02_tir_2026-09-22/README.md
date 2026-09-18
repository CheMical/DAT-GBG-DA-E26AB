# Design: User stories, Controller, Ansvar og afhængigheder, Coupling og Cohesion

## Beskrivelse

I de foregående lektioner har vi arbejdet med klasser, objekter, metoder og `ArrayList`. Vi har bygget projektet om bogsamling, hvor vi har lavet klasser som `Book` og `Library`.

I denne lektion tager vi et nyt skridt: ikke kun at få programmet til at fungere, men at spørge, hvordan koden er organiseret. Et program kan godt køre, men stadig være svært at forstå, ændre og udvide. Derfor arbejder vi med user stories, controller, ansvar, afhængigheder, coupling og cohesion.

Målet er, at vi lærer at strukturere koden, så hver klasse har et klart ansvar, og så flere klasser kan samarbejde uden at blive for tæt koblet sammen.

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

Engineering for Software • Dave Farley • YOW! 2022  
["Managing complexity"](https://www.youtube.com/watch?v=J8vCm1NdKIc&t=1931s)
(til slutningen af videoen)

## Læs nedenstående før undervisningen

Før lektionen bør du have genopfrisket:

- klasser og objekter
- metoder og tilstand
- `ArrayList` af egne objekter
- hvordan `Book` og `Library` samarbejder
- forskellen mellem en klasse, der beskriver data, og en klasse, der styrer flowet

## Udgangspunkt

Vi fortsætter med projektet om bogsamling, fordi det er det projekt, vi allerede har arbejdet med.

Vi har allerede set, at `Book` beskriver én bog, og at `Library` holder styr på mange bøger i en `ArrayList`.

Det giver os et godt udgangspunkt til at tale om design i stedet for kun kode.

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
import java.util.ArrayList;

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

Dette er vores udgangspunkt. Nu skal vi fokusere på, hvordan vi organiserer koden, så den bliver lettere at forstå, ændre og udvide.

## Aktiviteter i undervisningen

### User stories i bogsamling

En user story er en kort beskrivelse af en funktionalitet fra brugerens synspunkt. Den beskriver ikke, hvordan vi skal bygge løsningen, men hvad brugeren vil kunne gøre.

Vi skriver user stories i et simpelt format med tre dele:

- Bruger: hvem er det, der får værdi af funktionen?
- Handling: hvad vil brugeren kunne gøre?
- Grund / behov / værdi: hvorfor er det vigtigt for brugeren?

Formatet ser sådan ud:

- Som [bruger] vil jeg [handling], så [grund/behov/værdi].

Eksempler til bogsamlingen:

- Som bruger vil jeg kunne tilføje en bog, så jeg kan samle mine bøger.
- Som bruger vil jeg kunne finde en bog ud fra titel, så jeg hurtigt kan finde den rigtige bog.
- Som bruger vil jeg kunne markere en bog som læst, så jeg kan holde styr på, hvad jeg allerede har læst.
- Som bruger vil jeg kunne se alle bøger i min samling, så jeg får et overblik over mine bøger.

Det vigtigste i en user story er ikke teknikken, men den værdi, som brugeren får. Derfor er “grund / behov / værdi”-delen vigtig. Den fortæller, hvorfor funktionen overhovedet er relevant.

#### Acceptkriterier

Når vi skriver user stories, er det ofte nyttigt at tilføje acceptkriterier. Acceptkriterier er konkrete regler for, hvornår en funktion er færdig og fungerer som forventet. De gør user storyen mere præcis og lettere at teste.

Et acceptkriterium skrives ofte som:

- Givet [forudsætning], når [handling], så [resultat]

Eksempler til bogsamlingen:

- Givet at brugeren indtaster en titel, når der søges efter en bog, så skal programmet returnere den bog, der matcher titlen.
- Givet at bogen ikke findes, når brugeren søger, så skal programmet vise en passende besked.
- Givet at en bog er markeret som læst, når brugeren åbner bogens oplysninger, så skal den vises som læst.
- Givet at biblioteket er tomt, når brugeren vil se alle bøger, så skal programmet vise en tydelig besked om, at der ingen bøger er.

Acceptkriterier er nyttige, fordi de gør det tydeligt, hvad der skal være sandt, før vi kan sige, at en user story er løst.

#### Diskussion

- Hvilke user stories passer godt til projektet bogsamling?
- Hvad er den vigtigste del i en user story: bruger, handling eller grund/behov/værdi?
- Hvilke acceptkriterier ville du skrive til “find bog” eller “markér som læst”?
- Hvorfor er det nyttigt at have både en user story og acceptkriterier?

### Controller

Når vi har en brugerflade eller en konsolmenu, er controlleren den del, der styrer flowet. Den læser input, vælger den rette handling og kalder de metoder, der faktisk udfører arbejdet.

Et simpelt eksempel kunne være en `LibraryController`:

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

Her styrer controlleren menuen og brugerinput. Den bruger `Library` til at gøre selve arbejdet.

Det er vigtigt, at controlleren ikke bliver en stor “altmulig-mand”. Den skal styre flowet, ikke holde alle data og alle beslutninger selv.

#### En enkel opdeling i et konsolprogram

I et konsolprogram kan vi tænke om design på en enkel måde:

- Data/struktur: klasser, der beskriver problemområdet og holder information
- Controller: klassen, der styrer brugerinteraktionen og flowet
- Startpunkt: klassen, der sætter programmet i gang

I bogsamlingen betyder det for eksempel:

- `Book` og `Library` er data/struktur: de repræsenterer bogsamlingen og bogernes oplysninger
- `LibraryController` er controlleren: den læser input, viser menu og kalder de rigtige metoder
- `Main` er startpunktet: den opretter objekter og starter programmet

Dette er en praktisk og konkret måde at tænke om ansvar på, når vi endnu ikke har lært MVC (Model-View-Controller) som et formelt mønster. Vi fokuserer her på tydelige roller i programmet, ikke på en komplet arkitektur med flere lag.

### Ansvar og afhængigheder

Når vi designer klasser, bør vi altid spørge:

- Hvad er klassen ansvarlig for?
- Hvilken information skal den kende til?
- Hvilke metoder hører naturligt til klassen?
- Hvilke andre klasser bruger den?

Eksempler i bogsamlingen:

- `Book` har ansvar for at beskrive en bog: titel, forfatter og læsestatus
- `Library` har ansvar for at holde bogsamlingen og finde/tilføje/fjerne bøger
- `LibraryController` har ansvar for menuen og brugerinput
- `Main` har ansvar for at starte programmet og teste det

Hvis en klasse får for mange ansvar, bliver den svær at forstå og svær at ændre. Derfor er det vigtigt, at klasserne har tydelige roller.

Afhængigheder handler om, at klasser bruger hinanden. Det er normalt okay, men vi vil gerne holde afhængighederne så simple som muligt, så en ændring ikke påvirker for mange andre klasser.

### Coupling (kobling)

Coupling betyder, hvor tæt klasser er koblet sammen. I dansk kan vi også sige, at det handler om, hvor stærkt klasser er afhængige af hinanden.

- Lav kobling = klasserne er relativt uafhængige af hinanden
- Høj kobling = klasserne er meget afhængige af hinanden

Eksempel på høj kobling:

```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Book> books = new ArrayList<>();

        Book book = new Book("The Hobbit", "J.R.R. Tolkien");
        books.add(book);

        // meget kode her: søgning, visning, menu, validation, logging
    }
}
```

Her bliver `Main` ansvarlig for for mange ting. Koden bliver svær at læse, og tingene står meget tæt sammen.

Eksempel på lavere kobling:

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

### Cohesion (sammenhæng)

Cohesion handler om, hvor godt metoderne i en klasse arbejder sammen mod samme formål. I dansk kan vi også sige, at det handler om, hvor godt en klasse har en tydelig sammenhæng i sit indhold.

- Høj sammenhæng = klassen har et tydeligt formål
- Lav sammenhæng = klassen blandes med mange forskellige emner

Eksempel på lav sammenhæng:

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

Eksempel på høj sammenhæng:

```java
public class Library {
    public void addBook(Book book) { ... }
    public void findBookByTitle(String title) { ... }
    public void removeBook(String title) { ... }
    public void printBooks() { ... }
}
```

Her hører metoderne sammen: de arbejder alle med bibliotekets samling af bøger.

### Refaktoring af bogsamlingen

Det er vigtigt at være opmærksom på, når vi har for meget kode i én klasse.

Hvis vi starter med at have alt i `Main`, kan vi løbe ind i dette problem:

- opret bøger
- tilføj bøger til listen
- søg efter en bog
- vis alle bøger
- læs brugerinput
- vis menuer
- håndter valg

Det er meget i én klasse.

I stedet kan vi dele det op:

- `Book` beskriver en bog
- `Library` administrerer listen
- `LibraryController` styrer brugerinteraktionen
- `Main` starter programmet

Det gør koden mere overskuelig, lettere at teste og lettere at udvide.

### Opsamling

Design handler ikke kun om, hvordan koden ser ud, men om, hvordan den er organiseret. Når vi arbejder med user stories, controller, ansvar, afhængigheder, coupling og cohesion, så skaber vi kode, der er:

- lettere at læse
- lettere at ændre
- lettere at udvide
- mere robust i større programmer

Det er et vigtigt næste skridt i vores objektorienterede programmering, fordi det går fra at have kode, der virker, til at have kode, der er godt designet.

Det betyder også, at vi bliver bedre til at løse problemer, ikke kun at skrive funktioner. Vi lærer at tænke som udviklere, der planlægger og strukturerer et system, før det bliver for komplekst.

## Aktiviteter i undervisningen

Arbejd med disse [opgaver](opgaver.md).
