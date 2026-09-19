# Opgaver – Git og GitHub - introduktion til versionsstyring

## Kom i gang

Ny uge – opret et nyt IntelliJ-projekt eller en ny lokal mappe til Git-øvelserne, og opret dagens package:

```text
dag1_git_github_intro
```

Du skal kunne arbejde både lokalt og med GitHub. Brug enten terminalen eller IntelliJ’s Git-værktøjer, men hold dig til samme arbejdsproces gennem hele opgaveforløbet.

---

# Del 1 – Grundlæggende Git-koncepter

## Opgave 1 – Klon startprojektet via terminalen

I denne opgave skal du hente startprojektet ned på din computer ved hjælp af Git i terminalen.

### 1. Naviger til `IdeaProjects`

IntelliJ gemmer normalt dine projekter i mappen `IdeaProjects` i din brugermappe. Åbn din terminal:

- **Git Bash (Windows):**
  ```bash
  cd ~/IdeaProjects
  ```
  *(eller `cd /c/Users/<dit-brugernavn>/IdeaProjects`)*

- **Terminal (Mac):**
  ```bash
  cd ~/IdeaProjects
  ```

Tjek eventuelt med `pwd`, at du står i mappen `IdeaProjects`.

### 2. Klon projektet med Git

Klon repositoriet fra GitHub ved at køre:

```bash
git clone https://github.com/EK-DAT-GBG-1SEM-E26AB/Main.git
```

Naviger derefter ind i projektmappen:

```bash
cd Main
```

> **Bemærk:** Hvis du allerede har en mappe kaldet `Main`, får du muligvis en fejl (fordi mappen allerede eksisterer). Du kan tilføje et ekstra argument til `git clone`, hvor du angiver et nyt mappenavn som fx `Main-xyz`:
>
> ```bash
> git clone https://github.com/EK-DAT-GBG-1SEM-E26AB/Main.git Main-xyz
> cd Main-xyz
> ```

### 3. Diskussion og refleksion

Undersøg mappens indhold (f.eks. ved at køre `ls` i terminalen eller ved at inspicere mappen).

Diskuter derefter i gruppen:

- Hvad er det basalt set, du lige har downloadet fra GitHub?
- Hvilke filer og mapper har du fået ned på din computer?
- Hvad er formålet med de enkelte filer, du kan se?

*(Bemærk: Hvis du opdager en skjult mappe ved navn `.git`, kan du se bort fra den for nu – den kigger vi nærmere på i de næste opgaver).*

## Opgave 2 – Slet src-mappen og gendan med Git

I denne opgave undersøger du en af de mest basale styrker ved Git: muligheden for at genskabe tabte filer.

### 1. Slet `src`-mappen med bekræftelse

Slet nu `src`-mappen og dens indhold via terminalen. Vi bruger flaget `-i` (interactive) og `-r` (recursive), så du bliver bedt om at bekræfte hver sletning i stedet for at gennemtvinge den:

```bash
rm -ri src
```

Tast `y` (for *yes*) og tryk **Enter**, hver gang terminalen spørger, om en fil eller mappen skal slettes.

Når du er færdig, undersøg mappen (fx med `ls`). Se, at `src`-mappen er væk, og at mappen ellers er tom (kun den skjulte `.git`-mappe er tilbage).

### 2. Gendan med `git checkout`

Prøv nu at hente de slettede filer tilbage med kommandoen:

```bash
git checkout master
```

> **Tip til terminalen:** Du behøver ikke at skrive hele branch-navnet manuelt. Når du blot har skrevet `git checkout ` og derefter de første par bogstaver (fx `ma`), kan du trykke på **Tab-tasten** 1–3 gange. Terminalen vil så automatisk auto-udfylde branch-navnet for dig!

Kør derefter `ls` igen for at bekræfte, at `src`-mappen og alle filerne er vendt tilbage.

### 3. Diskussion og refleksion

Diskuter følgende i gruppen:

- Hvad skete der helt præcist, da du kørte `git checkout master`?
- Hvor kom filerne fra, når de lige var blevet slettet fra harddisken?
- Hvilken rolle spiller `.git`-mappen i denne sammenhæng?
- Hvorfor giver versionsstyring som Git en tryghed, når man arbejder på et projekt, sammenlignet med en almindelig mappe?

## Opgave 3 – Åbn projektet i IntelliJ og se Git-status

I denne opgave åbner du det klonede repository som et IntelliJ-projekt og undersøger, hvilke filer der er registreret som uversionsstyrede.

### 1. Åbn projektet i IntelliJ

1. Åbn IntelliJ.
2. Vælg **File → Open...**
3. Naviger til den mappe, du klonede i `IdeaProjects`.
4. Vælg projektmappen og åbn den som et IntelliJ-projekt.

### 2. Gå til Change-vinduet

Når projektet er åbnet, skal du finde **Git / Change**-vinduet i IntelliJ.

Se herefter efter sektionen **Unversioned Files**.

> **Vigtigt:** Denne sektion kan være foldet sammen. Klik på den for at udvide den, så du kan se hvilke filer der ligger der.

### 3. Diskussion og refleksion

Diskuter følgende i gruppen:

- Hvilke filer vises under `Unversioned Files`?
- Hvorfor er de ikke allerede versioneret i Git?
- Hvad betyder det, at en fil er "unversioned"?
- Hvem eller hvad har oprettet disse ekstra filer?
- Hvorfor er dette et nyttigt sted at se, når man lige har klonet et projekt eller har lavet nye filer lokalt?

## Opgave 4 – [overskrift]

## Opgave 5 – [overskrift]

## Opgave 6 – [overskrift]

---

# Del 3 – Commits, historik og workflow

## Opgave 7 – [overskrift]

## Opgave 8 – [overskrift]

## Opgave 9 – [overskrift]

---

## Ekstra

- [Skriv ekstra Git-øvelser her]
- [Skriv refleksionsspørgsmål om commit, staging og remote her]
- [Skriv optional opgaver om GitHub-flow her]
