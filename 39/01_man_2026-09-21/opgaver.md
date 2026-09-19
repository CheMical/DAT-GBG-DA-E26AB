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

## Opgave 2 – [overskrift]

## Opgave 3 – [overskrift]

---

# Del 2 – Repositorier og GitHub

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
