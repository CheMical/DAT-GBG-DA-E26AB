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

## Opgave 4 – Omdøb projektet i IntelliJ og undersøg Git-status

I denne opgave ændrer du navnet på projektmappen i IntelliJ for at få erfaring med, hvordan fil- og projektnavne påvirker et Git-repositorie.

### 1. Omdøb projektet i IntelliJ

1. I IntelliJ skal du gå til **Project-vinduet**.
2. Find projektmappen, der hedder `Main`.
3. Højreklik på mappen og vælg en mulighed for at omdøbe den.
4. Giv projektet et mere beskrivende navn, fx `Main-xyz`, `GitDemo` eller et andet passende navn.

### 2. Undersøg, hvad der sker

Når du har omdøbt projektet, skal du se nærmere på **Git / Change**-vinduet igen.

Diskuter følgende i gruppen:

- Hvad skete der med projektet, da du omdøbte mappen?
- Er Git opmærksom på den nye mappe-navngivning?
- Hvad sker der med kildekoden, når du omdøber projektet lokalt?
- Kan du stadig køre programmet efter omdøbningen?

### 3. Kør programmet igen

Prøv at køre projektet efter omdøbningen.

Besvar:

- Kørte programmet stadig uden problemer?
- Var der nogen ekstra trin nødvendige for at få det til at køre igen?

### 4. Er det nødvendigt at gemme ændringen i Git?

Tænk over:

- Er omdøbningen af en mappe en ændring i projektets indhold?
- Skal denne ændring gemmes i Git, eller er det blot en lokal ændring i din arbejdsmappe?
- Hvad er forskellen på at omdøbe en mappe lokalt og at committe en ændring til GitHub?

### 5. Lav et commit over ændringen

Hvis du har gjort en lokal ændring, fx omdøbt projektmappen, kan du også gemme den i Git.

I IntelliJ skal du:

1. Gå til **Git / Commit**
2. Vælg de filer, der er ændret
3. Skriv en passende commit-besked, fx:

```text
Omdøb projektmappe fra Main til et mere passende navn
```

4. Tryk på **Commit**-knappen.

Diskuter herefter:

- Hvad betyder det at "committe" en ændring?
- Hvorfor er det vigtigt at skrive en tydelig commit-besked?
- Hvordan kan en commit gøre det nemmere at holde styr på projektets historie?

## Opgave 5 – [overskrift]

## Opgave 6 – [overskrift]

## Opgave 7 – [overskrift]

---

# Del 3 – Commits, historik og workflow

## Opgave 8 – [overskrift]

## Opgave 9 – [overskrift]

## Opgave 10 – [overskrift]

---

## Ekstra

- [Skriv ekstra Git-øvelser her]
- [Skriv refleksionsspørgsmål om commit, staging og remote her]
- [Skriv optional opgaver om GitHub-flow her]
