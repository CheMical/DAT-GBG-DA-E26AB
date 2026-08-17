# Adventure del 4 – Weapons

> **Bunden forudsætning.** Del af det samlede [Adventure-projekt](readme.md).
>
> Det er her, **polymorfi** og **abstrakte klasser** kommer i spil for alvor.

## Beskrivelse

I skal arbejde videre på adventure-spillet. Spillet skal nu udvides med flere kommandoer, der giver
spilleren flere handlingsmuligheder, og et bredere udvalg af forskellige typer af våben.

## Læringsmål

Når du er færdig med denne del, skal du kunne:

* forklare hvad **polymorfi** er, og hvorfor det gør koden nemmere at udvide
* skrive en **abstrakt klasse**, der aldrig selv instantieres
* **override** en metode i en subklasse
* skrive kode, der kun kender superklassens type, men opfører sig forskelligt afhængigt af objektet
* forklare **hvorfor `instanceof` er et designproblem** her, og undgå det

---

## Krav

### Spillet

De ting, der ligger i rummene, skal enten blot være "ting", eller de skal være mad der kan spises,
eller **våben der kan bruges i angreb**.

Våben skal både kunne samles op og bæres rundt som alle items, men også **"equippes"** og være
klar til brug.

### Brugerfladen

Spillet skal udvides med kommandoen:

| Kommando | Betydning |
|---|---|
| `equip <våben>` | Gør det valgte våben fra spillerens inventory til det aktuelle |
| `attack` | Bruger det equippede våben (i denne udgave mod den tomme luft) |

#### equip

Hvis man skriver `equip` efterfulgt af noget, man ikke har i inventory, melder programmet blot, at
man ikke har sådan et våben.

Men hvis man har en ting med det navn, som blot **ikke er et våben**, skal programmet melde, at det
ikke er et våben.

Så **kun** hvis man har tingen, **og** tingen er et våben, kan det rent faktisk equippes.

> Man kan altså **ikke** equippe noget, der ligger i rummet!

#### attack

`attack` er i denne udgave en lidt "amputeret" kommando – da der ikke er nogle fjender endnu, vil
`attack` blot resultere i, at det våben, man har equipped, bliver brugt mod den tomme luft.

* Er det et **slagvåben**, sker der sandsynligvis ingenting.
* Er det et **skydevåben**, bliver der affyret et skud – hvis der altså er ammunition i våbenet.
* Prøver man at angribe med et **tømt våben**, skal man have at vide, at det mislykkedes.
* Har man **ikke et våben equipped**, skal man også have at vide, at det mislykkedes.

#### inventory

Derudover skal `inventory`-kommandoen udvides, så den også angiver, hvilket våben man aktuelt har
equipped.

Eksempel:

```text
> inventory
You are carrying: a shiny brass lamp, a rusty sword, an old revolver

> equip lamp
The shiny brass lamp is not a weapon

> equip revolver
You have equipped the old revolver

> inventory
You are carrying: a shiny brass lamp, a rusty sword, an old revolver
Equipped: an old revolver

> attack
You fire the old revolver into the empty air. 5 shots left.
```

### Koden

I har forventeligt allerede implementeret `Food`, og `Weapon` følger meget samme mønster: den skal
**arve fra `Item`**, så våben kan samles op, efterlades og bæres rundt, uden at resten af koden skal
ændres det mindste.

I `Map`, hvor rum og items oprettes, opretter I også de `Weapon`-objekter, der skal ligge rundt
omkring i spillet, og tilføjer dem til rooms, som var de almindelige items.

#### Weapon

`Weapon` skal have yderligere to arvinger:

* **`RangedWeapon`** – har et begrænset antal brug, før det "løber tør" og bliver ubrugeligt
* **`MeleeWeapon`** – kan normalt bruges et utal af gange

```mermaid
classDiagram
    class Item {
        -String longName
        -String shortName
    }
    class Weapon {
        <<abstract>>
        -int damage
        +getDamage() int
        +canUse() boolean
        +use() boolean
        +remainingUses() int
    }
    class MeleeWeapon
    class RangedWeapon {
        -int ammunition
    }

    Item <|-- Weapon
    Weapon <|-- MeleeWeapon
    Weapon <|-- RangedWeapon
```

#### Kun superklassen må kendes

Disse subklasser må **kun** bruges til at oprette våben i `Map` – alle andre steder må der kun
refereres til superklassen `Weapon`.

Altså: Når `Player` equipper et våben eller bruger det til `attack`, må koden kun tilgå metoder,
der er erklærede i `Weapon`-klassen.

Så hvis `RangedWeapon` skal kunne returnere, hvor mange skud der er tilbage, er der nødt til at
være en metode i `Weapon` (fx `remainingUses()` eller `canUse()`), der så **overrides** i
`RangedWeapon`.

> **Så altså: der må IKKE være noget kode, der tjekker typen af et weapon-objekt**, som f.eks.:
>
> ```java
> if (weapon instanceof RangedWeapon) { ... }   // ← NEJ
> ```
>
> Det er kun i `Map`, at der hentydes til de forskellige subklasser af `Weapon`.

#### Weapon er abstrakt

`Weapon` selv skal til gengæld **aldrig instantieres**. Der må ikke stå `new Weapon()` et eneste
sted i koden – kun subklasserne kan oprettes som objekter.

---

## Anbefalet procedure

Efter hvert trin skal I selvfølgelig teste, at spillet stadig virker som forventet.

1. **Opret de tre `Weapon`-klasser**, og tilføj forskellige våben i rummene, som spilleren kan
   samle op, som var de helt almindelige items.

2. **Tilføj `equip`-kommandoen** – brug samme princip som ved `eat`.

3. **Lav `attack`-kommandoen** uden at tage en parameter, men så spilleren blot attacker det tomme
   rum og for eksempel affyrer et skud (hvis det er et `RangedWeapon`).

   Forvent i første omgang at spilleren ikke attack'er uden at have equipped et weapon, og ikke
   affyrer det flere gange, end der er ammunition til.

4. **Håndter hvad der skal ske i `attack`**, hvis player ikke har equipped et weapon.

5. **Håndter hvad der skal ske i `attack`**, når våbenet er løbet tør for ammunition.

---

## Aflevering

Denne del indgår blot i samme GitHub-repository, som I hidtil har arbejdet i – og der er ikke krav
om aflevering som sådan, men **aflever gerne inden deadline, for at bekræfte at I er med!**

**Hvordan:** Indsæt et link til jeres GitHub-repository.

**Hvornår:** Inden del 5 starter – se
[deadlines i projektoversigten](readme.md#afleveringer-og-deadlines).

**Feedback:** Der er ikke planlagt nogen feedback på denne del – vi går direkte over i del 5!

---

## Øvelse til polymorfi

Til undervisningen hører denne øvelse, som træner polymorfi isoleret fra Adventure-projektet:

* **Polymorfi-øvelsen** – klasserne `Shape`, `Circle`, `Rectangle` og `Geometry`.
  Klon [Dat24v2_PolymorfiExercise](https://github.com/ETALATE/Dat24v2_PolymorfiExercise). Det meste
  af koden er fyldt ud i `Shape`, `Circle` og `Rectangle`, men `Geometry`-klassen, som holder på
  `main()`, er ufuldstændig – det er der, du kommer til at skrive mest.

---

**Næste:** [Del 5 – Enemies](del-5-enemies.md)
