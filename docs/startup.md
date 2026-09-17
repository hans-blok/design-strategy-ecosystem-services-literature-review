# Startup — aan de slag met agents in deze workspace

Voor Renske. Deze pagina legt uit wat een GitHub Agent is, wat je kunt voorbereiden, en hoe
je er zelf één maakt. Je hoeft niet te kunnen programmeren; je moet kunnen opschrijven wat
je wilt.

---

## 1. Waar dit over gaat

Dit project verwerkt ongeveer 120 wetenschappelijke artikelen. Van elk artikel leggen we drie
dingen vast: de design strategy, de ecosystem services en de locatie van de studie — telkens
met een citaat, een paginanummer en een inschatting van hoe zeker we zijn.

Dat soort werk zit vol herhaling: controleren of een record compleet is, kijken welke records
nog nagelopen moeten worden, samenvatten wat er al ingevuld is. Precies dat kun je aan een
agent overlaten.

---

## 2. Korte achtergrond: wat is een agent, en wat is een prompt?

### Een agent is een vastgelegde opdracht

Normaal typ je een vraag in een chatvenster. De volgende keer typ je hem opnieuw, net iets
anders, en krijg je een net iets ander antwoord. Een **agent** is diezelfde opdracht, maar
één keer goed opgeschreven en bewaard als bestand. Iedereen die hem aanroept krijgt dezelfde
werkwijze.

Een agent is een gewoon Markdown-bestand in de map `.github/agents/`, met de naam
`<agent-naam>.agent.md`. Bovenin staat een klein blokje met een naam en een omschrijving,
daaronder gewone tekst: de instructies. Die tekst is letterlijk wat de AI te lezen krijgt.

Denk aan een agent als een **functieomschrijving voor een collega**: wat is je taak, wat krijg
je aangeleverd, hoe pak je het aan, wat lever je op, en waar houdt je verantwoordelijkheid op.
Hoe scherper dat opgeschreven staat, hoe bruikbaarder het resultaat.

### Een prompt is alleen een snelkoppeling

Daarnaast bestaan er **prompt-bestanden**, in de map `.github/prompts/`, met de naam
`<agent-naam>.<wat-het-doet>.prompt.md`. Zo'n bestand bevat bijna niets: één regel uitleg en
de naam van de agent. Het bestaat alleen zodat je de agent kunt starten door in de chat een
`/` te typen en hem uit het lijstje te kiezen.

Dat onderscheid is belangrijk en wordt vaak door elkaar gehaald:

| | Waar | Wat erin staat |
|---|---|---|
| **Agent** | `.github/agents/` | Alle instructies. Dit is het echte werk. |
| **Prompt** | `.github/prompts/` | Alleen een verwijzing naar de agent. Drie regels. |

Gooi je het promptbestand weg, dan verlies je niets behalve het gemak van het `/`-menu. Gooi
je het agent-bestand weg, dan ben je alles kwijt.

### Waar werkt het?

Prompt-bestanden worden gelezen door **Copilot Chat in VS Code** (en in Visual Studio en
JetBrains). Op github.com werken ze niet, en Claude Code leest die map ook niet — dat gebruikt
een eigen map, `.claude/commands/`.

Dus: gebeurt er niets als je `/` typt, dan zit je waarschijnlijk in het verkeerde venster. Dat
is de meest gemaakte beginnersfout en het kost mensen makkelijk een half uur.

---

## 3. Wat je kunt voorbereiden

### Lees het sjabloon

Lees eerst [`templates/agent.template.md`](https://github.com/hans-blok/design-strategy-ecosystem-services-literature-review/blob/main/templates/agent.template.md) van boven naar
beneden. Eén keer, rustig, zonder iets in te vullen.

Dat sjabloon is de kern van deze workspace. Het stelt in vaste volgorde de vragen die samen
een goede agent opleveren:

1. **Verantwoordelijkheid** — wat is de taak, in één alinea?
2. **Input** — wat krijgt de functie binnen, waar komt dat vandaan, en wat moet er minimaal
   aanwezig zijn om verantwoord te kunnen beginnen?
3. **What it does** — welk werk wordt er met die input gedaan?
4. **How it works** — in welke stappen?
5. **Concepts** — welke afgesproken begrippen doen ertoe? (Alleen benoemen, niet uitleggen.)
6. **Rules** — welke vastgelegde regels gelden? (Alleen verwijzen, niet overschrijven.)
7. **Output** — wat komt eruit, en hoe ziet dat eruit?
8. **Wat het níét doet** — waar houdt het op?

Je hoeft die volgorde niet uit je hoofd te kennen. Het gaat erom dat je de denkwijze herkent:
*wat krijg ik, wat doe ik ermee, wat lever ik op, en waar stop ik.*

Twee secties lichten we eruit, omdat ze het minst vanzelfsprekend zijn:

- **Concepts** — hier zet je alleen de naam van een begrip, niet de definitie. De definitie
  staat ergens anders en verandert soms; een kopie in jouw bestand veroudert dan stilletjes.
  Vaak is het antwoord gewoon "None."
- **Rules** — hetzelfde idee: verwijs naar de regel met zijn kenmerk en het bestand waar hij
  staat, in plaats van de tekst over te nemen.

### Kijk waar het schema staat

Open [`schemas/paper.schema.json`](https://github.com/hans-blok/design-strategy-ecosystem-services-literature-review/blob/main/schemas/paper.schema.json). Dat bestand beschrijft hoe een
ingevuld artikel-record eruit moet zien: welke velden verplicht zijn, dat elk citaat een
paginanummer nodig heeft, en dat `confidence` alleen `low`, `medium` of `high` mag zijn.

Veel agents die je hier maakt zullen naar dat bestand verwijzen. Je hoeft het niet tot op de
komma te begrijpen — wel te weten dat het bestaat en wat het afdwingt.

### Bedenk één concrete klus

Niet "iets met AI voor mijn onderzoek", maar één afgebakende, terugkerende handeling waarvan
je nu al weet hoe het goede antwoord eruitziet. Bijvoorbeeld: *welke records zijn nog niet
compleet?* Dat je het antwoord kunt herkennen, maakt de eerste agent tot een goede oefening.

---

## 4. Handleiding: zelf een agent maken

Je hoeft het sjabloon niet met de hand in te vullen. Er is een agent die dat samen met jou
doet: de **agent-designer**.

### Stap 1 — Open Copilot Chat in VS Code

Typ `/` en kies `agent-designer.design-agent`.

### Stap 2 — Beschrijf wat je wilt

Gebruik het invulformulier uit de [README](https://github.com/hans-blok/design-strategy-ecosystem-services-literature-review/blob/main/README.md). Vul in wat je weet en laat de rest
leeg:

```text
Doel (één zin):
Verantwoordelijkheid:
Input:
Output:
Heeft toegang nodig tot:
Mag niet:
```

Twee antwoorden zijn onmisbaar: **het doel** en **hoe de output eruitziet**. De rest kan de
designer afleiden of navragen. Bij de overige velden mag je gerust "weet ik nog niet" zetten —
daar stelt hij dan een vraag over.

### Stap 3 — Beantwoord zijn vragen

De designer stelt alleen vragen als er echt iets ontbreekt. Waar hij een aanname doet, zegt
hij dat erbij. Lees die aannames na: klopt er eentje niet, corrigeer hem dan meteen, en niet
pas nadat het bestand er staat.

### Stap 4 — Lees de uitleg

Je krijgt niet alleen een bestand terug, maar ook een korte toelichting op de keuzes die niet
vanzelf spreken. Dat is het leerzaamste deel. De tweede agent maak je een stuk makkelijker dan
de eerste, mits je die uitleg leest.

### Stap 5 — Probeer hem uit

Roep je nieuwe agent aan en kijk of het antwoord klopt. Klopt het niet, dan hoef je meestal
niet opnieuw te beginnen: pas de instructietekst in het `.agent.md`-bestand aan. Het is gewone
tekst, je mag er zelf in schrijven.

---

## 5. Waar het meestal misgaat

- **Te veel tegelijk.** Moet je "en" twee keer gebruiken om de taak te beschrijven, dan zijn
  het waarschijnlijk twee agents. Eén taak per agent.
- **Te vaag.** "Controleer de data zorgvuldig" levert een willekeurig antwoord op.
  "Controleer of elk record een `page` heeft en noem de records waar dat ontbreekt" niet.
- **Niet gezegd hoe de output eruitziet.** Geef één voorbeeldregel. Dat scheelt meer dan een
  alinea uitleg.
- **Niet gezegd wat er níét mag.** Zet erbij dat de agent geen bestanden mag wijzigen, als je
  alleen een rapportage wilt.
- **Definities overschrijven.** Verwijs naar het schema of naar een regel; neem de inhoud niet
  over. Kopieën verouderen.
- **Verkeerd venster.** Zie hierboven: het `/`-menu met prompts werkt in Copilot Chat, niet
  overal.

---

## 6. Een eerste oefening

Maak een agent die de records in `papers/` controleert tegen `schemas/paper.schema.json` en
rapporteert welke records incompleet zijn of nog nagekeken moeten worden.

Waarom juist deze: je weet vooraf hoe het antwoord eruit hoort te zien, het is echt werk dat
anders met de hand gebeurt, en hij verandert niets — dus je kunt niets stukmaken terwijl je
oefent.

Lukt dat, dan heb je de hele keten één keer doorlopen: taak afbakenen, input benoemen, output
beschrijven, grenzen stellen, uitproberen. Alles daarna is variatie op datzelfde patroon.
