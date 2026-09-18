# Git og GitHub - introduktion til versionsstyring

## Beskrivelse

I denne undervisningsgang introduceres du til Git og GitHub, som er blandt de mest anvendte værktøjer til versionsstyring inden for softwareudvikling.

Måske har du tidligere anvendt OneDrive, Google Drive eller Dropbox til at gemme filer og holde styr på ændringer. Disse tjenester kan gemme tidligere versioner og synkronisere filer, men Git er udviklet specifikt til at holde styr på ændringer i blandt andet kildekode.

Forestil dig følgende filer:

```text
Projekt.java
Projekt_v2.java
Projekt_final.java
Projekt_final_v2.java
Projekt_final_v2_rigtig.java
```

Det bliver hurtigt vanskeligt at afgøre, hvilken fil der er den rigtige, hvad der er ændret, og hvorfor ændringen blev foretaget. Git løser dette ved at gemme projektets udvikling som en sammenhængende historik.

Git og GitHub er ikke det samme:

- **Git** er et versionsstyringssystem, som kører på din computer.
- **GitHub** er en onlinetjeneste, hvor Git-repositories kan opbevares og deles.

Materialet forudsætter, at du allerede har oprettet en konto på GitHub og installeret Git Bash eller et tilsvarende terminalprogram på Windows eller Mac.

## Læringsmål

Når du har arbejdet med dagens materiale, skal du kunne:

- forklare formålet med versionsstyring
- forklare forskellen mellem Git og GitHub
- forklare hvad et repositorie er
- oprette et lokalt Git-repositorie
- oprette et repositorie på GitHub
- forbinde et lokalt repositorie med et repositorie på GitHub
- hente et repositorie fra GitHub til din computer
- forklare hvad staging og commits er
- oprette commits med beskrivende commit-beskeder
- vise projektets commit-historik

## Se disse videoer før undervisningen

Hvis Git ikke allerede er installeret på din computer, så se denne video først:  
[A brief introduction to Git for beginners | GitHub](https://www.youtube.com/watch?v=r8jQ9hVA2qs)

Om git:  
[What is Version Control?](https://git-scm.com/videos/what-is-version-control) (05:59)  
[What is Git?](https://git-scm.com/videos/what-is-git) (08:15)  
[Get Going with Git](https://git-scm.com/videos/get-going-with-git) (04:26)  
[Quick Wins with Git](https://git-scm.com/videos/quick-wins-with-git) (05:06)

Om GitHub:  
[How to create your first GitHub repository: A beginner's guide | Tutorial](https://www.youtube.com/watch?v=-RZ03WHqkaY)  
[How to upload files and folders to GitHub: GitHub for Beginners](https://www.youtube.com/watch?v=tlu5e0TxSzo)

## Grundlæggende begreber

Læs disse afsnit for at forstå de vigtigste Git-koncepter, før du går i gang med praktiske opgaver.

### Versionsstyring i hverdagen

Du kender muligvis allerede versionsstyring fra OneDrive eller Google Drive. Når du redigerer et dokument, gemmer tjenesten ændringerne og kan i nogle tilfælde vise tidligere versioner.

Git arbejder med den samme grundidé, men giver udvikleren mere kontrol. Du vælger selv, hvornår en meningsfuld version skal gemmes, og du skriver en kort besked om ændringen.

En gemt version i Git kaldes en **commit**.

Der er også en vigtig forskel på synkronisering og versionsstyring. OneDrive forsøger normalt at holde en fil på din computer synkroniseret med en fil i skyen. Git gemmer derimod en historik af udvalgte ændringer. Ændringerne sendes ikke automatisk til GitHub. Du bestemmer selv, hvornår de skal sendes.

### Hvad er Git?

Git er et distribueret versionsstyringssystem. Det betyder, at projektet og dets historik kan ligge lokalt på din computer. Du behøver derfor ikke GitHub for at bruge Git.

Git kan blandt andet hjælpe med at:

- gemme projektets udvikling
- vise hvilke filer der er ændret
- dokumentere ændringer med commit-beskeder
- vende tilbage til tidligere versioner
- udveksle ændringer med andre udviklere

### Hvad er et repositorie?

Et Git-projekt kaldes et **repositorie**, ofte forkortet til **repo**.

Et lokalt repositorie består af projektets almindelige filer og en skjult mappe med navnet `.git`. Den skjulte mappe indeholder Git-historikken og oplysninger om repositoriet.

Du skal normalt ikke ændre indholdet af `.git` manuelt.

### Hvad er GitHub?

GitHub er en onlinetjeneste til opbevaring og deling af Git-repositorier. Et repositorie på GitHub kaldes ofte et **remote repositorie**, fordi det ligger et andet sted end den lokale kopi på din computer.

Et repositorie kan derfor eksistere:

1. kun lokalt på din computer
2. kun på GitHub
3. både lokalt og på GitHub

I praksis vil man ofte have både en lokal kopi og en kopi på GitHub.

### Git Bash og terminalen

Git Bash giver på Windows adgang til Git-kommandoer i en terminal. På Mac kan de samme Git-kommandoer anvendes i Terminal eller et tilsvarende program.

En terminal viser normalt den mappe, du står i. Før du bruger en Git-kommando, skal du derfor kontrollere, at terminalen står i den rigtige projektmappe.

Du kan se den aktuelle mappe med:

```bash
pwd
```

Du kan se mappens indhold med:

```bash
ls
```

Du kan skifte mappe med:

```bash
cd mappenavn
```

IntelliJ opretter typisk en mappe med navnet `IdeaProjects` i din hjemmemappe, og det er her IntelliJ lægger projekter, du opretter i IDE'et. På Windows kan den typisk ligge i:

```text
C:\Users\mica\IdeaProjects
```

I Git Bash vises den normalt som:

```bash
/c/Users/mica/IdeaProjects
```

Eksempel på brug i terminalen:

```bash
pwd
ls
cd /c/Users/mica/IdeaProjects
ls
```

## Opret dit første repositorie

Du kan oprette et repositorie på to måder: via terminalen eller via IntelliJ. Vælg den metode, du er mest komfortabel med.

### Vejledning A: Opret repositorie via Terminal

#### Opret en projektmappe

Opret en ny mappe og gå ind i den:

```bash
mkdir mit-forste-repository
cd mit-forste-repository
```

#### Initialiser Git

Gør mappen til et Git-repositorie:

```bash
git init
```

Git opretter nu den skjulte mappe `.git`. De almindelige projektfiler ændres ikke.

Kontrollér repositoriets status:

```bash
git status
```

`git status` er en af de vigtigste Git-kommandoer. Den fortæller blandt andet:

- hvilken branch du står på
- hvilke filer Git endnu ikke følger
- hvilke filer der er ændret
- hvilke ændringer der er gjort klar til næste commit

#### Opret en fil

Opret filen `README.md` i mappen. Du kan gøre det i IntelliJ eller med en almindelig teksteditor.

Skriv eksempelvis:

```markdown
# Mit første repositorie

Dette repositorie bruges til at lære Git.
```

Kør derefter:

```bash
git status
```

Git viser nu `README.md` som en fil, der endnu ikke spores.

### Vejledning B: Opret repositorie via IntelliJ

Hvis du foretrækker at oprette projektet direkte i IntelliJ, kan du gøre det uden først at bruge terminalen.

#### Opret et projekt

1. Åbn IntelliJ.
2. Klik på `File` → `New` → `Project`.
3. Vælg en mappe, hvor projektet skal ligge.
4. Angiv et projektnavn, fx `mit-forste-repositorie`.
5. **Vigtig:** I Project Creation-dialogen finder du en checkbox med teksten `Create Git Repository`.
6. **Afmærk denne boks**, så Git aktiveres automatisk under projekt-oprettelsen.
7. Klik på `Create`.

IntelliJ opretter nu projektet i en lokal mappe på din computer **og** initialiserer Git automatisk.

**Uden checkboxen:**

Hvis du ikke markerede `Create Git Repository` under oprettelsen, kan du aktivere Git efterfølgende:

1. Gå til menuen øverst i IntelliJ (hvis der ikke er Git aktiveret, hedder den `VCS`)
2. Klik `Enable Version Control Integration...`
3. Vælg `Git` fra dropdown-menuen
4. Klik på `OK`

Når Git er aktiveret, ændres menunavnet fra `VCS` til `Git`.

**Om Git-menuen:**

Efter Git er aktiveret, vil du bemærke at menuen øverst i IntelliJ hedder `Git` i stedet for `VCS`. Alle kommandoer i denne guide bruger `Git` → `...` fordi vi forudsætter, at Git er aktiveret. Hvis menuen stadig hedder `VCS`, betyder det, at Git endnu ikke er aktiveret i projektet.

#### Forstå Git-status i IntelliJ

Når Git er aktiveret, vil IntelliJ markere dine filer med farver i Project View:

- **Rød:** Filer som Git ikke følger endnu (utrackede filer)
- **Blå:** Filer som er blevet ændret siden sidste commit
- **Grøn:** Filer som er tilføjet til staging area (klar til commit)
- **Grå:** Filer som er ignoreret (fx i `.gitignore`)

Du kan også åbne **Changes**-vinduet for at se alle ændringer samlet:

- `Git` → `View Git Status` eller
- `Alt+9` (Windows) / `Cmd+9` (Mac)

#### Opret en fil og lav din første commit

1. Højreklik på dit projekt i Project View → `New` → `File`
2. Navngiv den `README.md`
3. Skriv indhold, fx:

```markdown
# Mit første repositorie

Dette repositorie bruges til at lære Git.
```

4. Du ser nu, at `README.md` er markeret i rødt (eller en anden farve for utrackede filer).
5. Højreklik på filen → `Git` → `Add`
6. Filen er nu markeret i grønt og er klar til commit.
7. Gå til `Git` → `Commit` (eller brug `Ctrl+K` eller `Alt+0` på Windows)
8. Skriv en god commit-besked: `Tilføj introduktion til projektet`
9. Klik på `Commit`

Committen er nu gemt lokalt i dit repositorie.

#### Alternativ: Brug terminalen

Du kan også fortsætte med at bruge terminalen direkte i IntelliJ:

1. Åbn terminalen nederst: `View` → `Tool Windows` → `Terminal` eller `Alt+F12`
2. Kør de samme Git-kommandoer som normalt:

```bash
git status
git add .
git commit -m "Tilføj introduktion til projektet"
```

**Det vigtigste er princippet:** Du har et lokalt repositorie, du laver commits, og senere kan du koble det til GitHub. Valget mellem GUI og terminal er helt op til dig.

## Forbind dit repositorie med GitHub

### To veje til GitHub

Der er to måder at få dit repositorie på GitHub:

**Vej 1: Opret på GitHub først, derefter klon lokalt**

Et repositorie kan oprettes på GitHub først og derefter hentes til computeren.

Når du opretter repositoriet på GitHub, skal du blandt andet vælge:

- et navn
- om repositoriet skal være offentligt eller privat
- om GitHub skal oprette en README-fil

Hvis repositoriet oprettes med en README-fil, indeholder det allerede en commit. Den enkleste måde at få det ned på computeren er derfor at klone det.

Kopiér repositoriets URL fra GitHub, og kør:

```bash
git clone <repository-url>
```

Eksempel på kommandoens form:

```bash
git clone https://github.com/brugernavn/repository-navn.git
```

Erstat adressen med URL'en til dit eget repositorie.

`git clone`:

- opretter en lokal mappe
- henter filerne
- henter commit-historikken
- forbinder den lokale kopi med repositoriet på GitHub

Gå derefter ind i den hentede mappe:

```bash
cd repository-navn
```

**Vej 2: Opret lokalt først, derefter push til GitHub**

Hvis repositoriet blev oprettet lokalt først, skal der oprettes et tomt repositorie på GitHub. Undlad i dette tilfælde at få GitHub til at oprette README, licens eller `.gitignore`, da det ellers ikke er helt tomt.

Knyt derefter det lokale repositorie til adressen på GitHub:

```bash
git remote add origin <repository-url>
```

Navnet `origin` er det almindelige navn for det primære remote repositorie.

Kontrollér forbindelsen:

```bash
git remote -v
```

Når der er oprettet mindst én lokal commit, kan den sendes til GitHub:

```bash
git push -u origin main
```

Indstillingen `-u` opretter forbindelsen mellem den lokale `main`-branch og `main` på GitHub. Senere vil det normalt være nok at skrive:

```bash
git push
```

### Forbind med GitHub via IntelliJ

Du kan også forbinde dit repositorie til GitHub direkte fra IntelliJ uden at bruge terminalen.

#### Vej 1: Clone fra GitHub direkte i IntelliJ

1. Fra IntelliJ startskærm, klik `Get from VCS` eller gå til `File` → `New` → `Project from Version Control`
2. Vælg `Git` som version control system
3. Indsæt repositoriets URL fra GitHub i feltet `URL`
4. Vælg en lokal mappe, hvor projektet skal ligges
5. Klik `Clone`

IntelliJ henter nu repositoriet, al historikken, og sætter forbindelsen til GitHub op automatisk.

Du kan nu se `.git`-mappen i dit projekt, og Git er fuldt integreret i IntelliJ.

#### Vej 2: Push lokalt projekt til GitHub

Hvis dit projekt allerede er lokalt:

1. Opret et tomt repositorie på GitHub (ingen README, licens eller `.gitignore`)
2. I IntelliJ, gå til `Git` → `Manage Remotes...`
3. Klik `+` (tilføj remote)
4. Sæt navn til `origin`
5. Indsæt GitHub repositoriets URL
6. Klik `OK`

Nu kan du pushe dit projekt til GitHub:

1. Gå til `Git` → `Push` (eller brug `Ctrl+Shift+K`)
2. Vælg de branches du vil pushe (typisk `main`)
3. Klik `Push`

Dit lokale projekt er nu upload til GitHub, og de er forbundet.

## Commits

En commit er en navngivet registrering af en meningsfuld ændring i projektet. Den kan sammenlignes med et øjebliksbillede, men Git gemmer ændringen som en del af projektets samlede historik.

Arbejdet frem mod en commit kan forstås i tre områder:

```text
Arbejdsmappe  ->  Staging area  ->  Repository
   git add          git commit
```

- **Arbejdsmappe:** De filer, du arbejder med.
- **Staging area:** De ændringer, der er valgt til næste commit.
- **Repository:** Den gemte commit-historik.

### Se ændringerne

Start altid med:

```bash
git status
```

**I IntelliJ:**
- Åbn **Changes**-vinduet: `Git` → `View Git Status` eller `Alt+9`
- Her ser du alle filer grupperet efter status:
  - **Unversioned Files:** Filer som Git ikke følger (som `git status` viser som "Untracked")
  - **Modified:** Ændrede filer
  - **Added:** Filer som er tilføjet til staging area

Du kan også se filernes farver direkte i Project View (rød = utrackede, blå = ændrede, grøn = staged).

### Gør en fil klar til commit

En bestemt fil tilføjes til staging area med:

```bash
git add README.md
```

Alle aktuelle ændringer i mappen kan tilføjes med:

```bash
git add .
```

Punktummet betyder den aktuelle mappe. Som begynder er det en god vane at køre `git status` både før og efter `git add .`, så du kan se, hvad der kommer med.

**I IntelliJ:**
- Højreklik på en fil i Project View
- Vælg `Git` → `Add`

Eller i Changes-vinduet:
- Marker de filer du vil tilføje
- Højreklik og vælg `Git` → `Add to Index` eller klik på pilen for at flytte filen til staging area

### Opret en commit

Når de rigtige ændringer er gjort klar, oprettes committen:

```bash
git commit -m "Tilføj introduktion til projektet"
```

Teksten efter `-m` er commit-beskeden.

En god commit-besked beskriver kort, hvad ændringen gør:

```text
Tilføj introduktion til projektet
Ret fejl i beregning af pris
Opret klasse til bøger
```

Disse beskeder er mindre nyttige:

```text
fix
ting
ændringer
færdig
```

**I IntelliJ:**
1. Gå til `Git` → `Commit` eller brug `Ctrl+K` eller `Alt+0` (Windows)
2. Commit-dialogen åbnes
3. Du ser alle ændringer som skal committes (kun staged filer)
4. Skriv commit-beskeden i tekstfeltet øverst
5. Klik `Commit` eller `Commit and Push` hvis du vil pushe samtidig

Du kan også tilføje filer direkte fra Commit-dialogen ved at markere dem i listen.

### Lav små, sammenhængende commits

En commit bør samle ændringer, der hører naturligt sammen. Hvis du både retter en fejl, omdøber en klasse og skriver dokumentation, kan det være mere overskueligt at lave flere commits.

En nyttig rytme er:

1. Foretag én sammenhængende ændring.
2. Kør `git status` (eller åbn Changes-vinduet).
3. Tilføj de relevante filer med `git add` (eller via GUI).
4. Opret en commit med en præcis besked.
5. Send senere commits til GitHub med `git push`.

### Se commit-historikken

Vis historikken med:

```bash
git log
```

En kortere visning fås med:

```bash
git log --oneline
```

Hver commit har et entydigt id, en forfatter, et tidspunkt og en commit-besked.

**I IntelliJ:**
1. Gå til `Git` → `Show History` eller brug `Alt+E` (på nogle systemer)
2. Eller højreklik på en fil i Project View → `Git` → `Show History`
3. Et History-vindue åbnes som viser alle commits for denne fil (eller hele repositoriet)
4. Du kan klikke på hver commit for at se ændringerne
5. Du kan også høreklikke på en commit for at se flere muligheder (f.eks. revert, cherry-pick osv.)

Du kan også se hele repositoriets historik ved at højreklikke på projektmappen → `Git` → `Show History`.

## Arbejdsflowet: Fra lokalt til GitHub

Når du arbejder med Git, bevæger dine ændringer sig gennem flere stadier:

```text
┌───────────────────────────────────────────────────────────────┐
│                       DIN COMPUTER                            │
│                                                               │
│    Arbejdsmappe  →  Staging area  →  Lokalt repositorie       │
│    (Dine filer)       (git add)        (git commit)           │
│                                             ↓                 │
│                                        git push               │
└───────────────────────────────────────────────────────────────┘
                             ↓
┌───────────────────────────────────────────────────────────────┐
│                          GITHUB                               │
│                                                               │
│                     Remote repositorie                        │
│                   (Dit projekt online)                        │
│                             ↓                                 │
│                         git pull                              │
└───────────────────────────────────────────────────────────────┘
                             ↓
              Tilbage til din arbejdsmappe
```

**Flowet:**
1. **Arbejdsmappe:** Du ændrer dine filer.
2. **Staging area:** Du vælger hvilke ændringer der skal med (`git add`).
3. **Lokalt repositorie:** Du gemmer ændringerne (`git commit`).
4. **GitHub:** Du sender dine commits til GitHub (`git push`).
5. **Hentning:** Du kan hente andres ændringer fra GitHub (`git pull`).

## Den grundlæggende arbejdsgang

Når repositoriet allerede er oprettet og forbundet med GitHub, vil en almindelig arbejdsgang være:

```bash
git status
git add .
git commit -m "Beskriv ændringen"
git push
```

Kommandoerne har forskellige opgaver:

- `git status` undersøger situationen.
- `git add` vælger ændringer til næste commit.
- `git commit` gemmer ændringerne lokalt i historikken.
- `git push` sender lokale commits til GitHub.

Hvis andre har lavet ændringer på GitHub, som du skal hente ned til din computer, kan du bruge:

```bash
git pull
```

`git pull` henter de nyeste ændringer fra GitHub og merger dem ind i dit lokale arbejde.

Det er vigtigt at forstå, at `git commit` ikke sender noget til GitHub. Committen oprettes lokalt. Først med `git push` bliver den sendt til det tilknyttede remote repositorie.

## Workflow i IntelliJ

Hvis du foretrækker at arbejde helt i IntelliJ uden at bruge terminalen, er her en typisk arbejdsgang:

### 1. Se ændringerne (git status)

Åbn Changes-vinduet:
- `Git` → `View Git Status` eller `Alt+9`

Du ser alle ændringer grupperet efter status. De filer som skal committes, er under "Staged" eller "Modified".

### 2. Tilføj filer til staging area (git add)

I Changes-vinduet:
- Marker de filer du vil committes
- Klik på pilen `→` eller højreklik → `Git` → `Add to Index`

Filerne flyttes nu til "Staged"-sektionen.

**Alternativt i Project View:**
- Højreklik på en fil → `Git` → `Add`

### 3. Opret en commit (git commit)

1. Tryk `Ctrl+K` eller `Alt+0` (Windows), eller gå til `Git` → `Commit`
2. **Commit**-dialogen åbnes
3. Skriv commit-beskeden i tekstfeltet øverst
4. Hvis der er filer i "Unstaged Changes", skal du enten:
   - Markere dem og klikke på `+` for at stage dem først, eller
   - Klikke på "Amend" hvis du vil tilføje dem til den forrige commit
5. Klik `Commit`

Committen er nu gemt lokalt.

### 4. Push til GitHub (git push)

1. Gå til `Git` → `Push` eller brug `Ctrl+Shift+K`
2. Vælg den branch du vil pushe (typisk `main`)
3. Klik `Push`

Dine commits er nu sendt til GitHub.

### 5. Hent ændringer fra GitHub (git pull)

1. Gå til `Git` → `Pull` eller brug `Ctrl+Alt+L`
2. IntelliJ henter de nyeste ændringer fra GitHub
3. Hvis der er konflikter, vises de i en merge-dialog

**Hele flowet på en gang:**

Du kan også kombinere Commit og Push:
1. Tryk `Ctrl+K` for at åbne Commit-dialogen
2. I stedet for at klikke `Commit`, kan du klikke `Commit and Push`
3. Begge handlinger udføres sekvens

## Det vigtigste at tage med

- Git og GitHub er ikke det samme.
- Git holder styr på projektets historik.
- GitHub kan opbevare og dele Git-repositorier online.
- Et Git-projekt kaldes et repositorie.
- `git init` opretter et repositorie i en eksisterende lokal mappe.
- `git clone` henter et eksisterende repositorie og dets historik.
- `git status` viser repositoriets aktuelle tilstand.
- `git add` vælger ændringer til næste commit.
- `git commit` gemmer ændringer lokalt i historikken.
- `git push` sender commits til GitHub.
- `git pull` henter ændringer fra GitHub til din computer.
- Små commits med præcise beskeder gør historikken lettere at forstå.

## Terminal-kommandoer vs. IntelliJ

Her er en hurtig reference til de vigtigste Git-kommandoer og deres ækvivalenter i IntelliJ:

| Opgave | Terminal | IntelliJ |
|--------|----------|----------|
| **Se status** | `git status` | `Git` → `View Git Status` (`Alt+9`) eller Changes-vinduet |
| **Tilføj en fil** | `git add fil.java` | Højreklik på fil → `Git` → `Add` |
| **Tilføj alle filer** | `git add .` | I Changes-vinduet: vælg alle files og `Git` → `Add to Index` |
| **Opret commit** | `git commit -m "besked"` | `Git` → `Commit` (`Ctrl+K` eller `Alt+0`), skriv besked, klik `Commit` |
| **Commit & Push** | `git commit -m "..."` + `git push` | `Git` → `Commit`, klik `Commit and Push` |
| **Push til GitHub** | `git push` | `Git` → `Push` (`Ctrl+Shift+K`) |
| **Pull fra GitHub** | `git pull` | `Git` → `Pull` (`Ctrl+Alt+L`) |
| **Se historik** | `git log` eller `git log --oneline` | `Git` → `Show History` (`Alt+E`) eller højreklik på fil/projekt → `Git` → `Show History` |
| **Klone repo** | `git clone <url>` | `File` → `New` → `Project from Version Control`, vælg `Git`, indsæt URL |
| **Opret lokalt repo** | `git init` | Markér `Create Git Repository` når du opretter projektet, eller gå til `Git` → `Enable Version Control Integration...` |
| **Forbind til GitHub** | `git remote add origin <url>` | `Git` → `Manage Remotes...`, klik `+`, tilføj `origin` og URL |

## Aktiviteter i undervisningen

De praktiske opgaver til undervisningsgangen findes i [opgaver.md](opgaver.md).
