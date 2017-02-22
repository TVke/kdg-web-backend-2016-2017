# GIT crash course

- De onderstaande commands zijn voor de [Git-CLI](https://git-scm.com/) in samenwerking met [GitHub](https://www.github.com). Je hebt dus een beetje kennis nodig van de command line tool.
- Je kan gebruik maken van Git-GUI's ([GitGIU](https://git-scm.com/docs/git-gui), [SourceTree](https://www.sourcetreeapp.com/)), maar het is beter om eerst te weten wat de basiscommando's zijn vooraleer je je hier aan waagt.
- Enkele interessante Git-tutorials:
  - [Try Git - interactive tutorial](https://try.github.io)
  - [The beginner's guide to contributing to a GitHub project](https://akrabat.com/the-beginners-guide-to-contributing-to-a-github-project/)
  

## Wat is Git?

Een gedistribueerd versiebeheersysteem. 

Versiebeheer laat je toe om verschillende versies van een applicatie bij te houden, zodat je makkelijk naar een vorige versie kan teruggrijpen. Het staat je ook toe om met een team aan één applicatie te werken, zonder dat je daarbij elkaars werk overschrijft. 

Gedistribueerd betekent dat iedereen een kopie heeft van de originele applicatie, in tegenstelling met gecentraliseerd versiebeheersysteem, waarbij iedereen dezelfde "master"-versie heeft. Gecentraliseerd versiebeheer heeft enorm veel nadelen ([Linus Torvalds, de uitvinder van het distribueerde systeem, legt uit waarom](https://www.youtube.com/watch?v=4XpnKHJAok8)) en zou dus niet meer mogen gebruikt worden.

## Git installeren

Voor Linux en Mac gebruikers is het makkelijk, daar is Git standaard geïnstalleerd. Windows-gebruikers moeten dit expliciet installeren. Surf naar [Git-SCM](https://git-scm.com/) en download de juiste versie.

Verder moet je er zeker van zijn dat je bij de installatie Git toevoegt aan je PATH-variabele. Als je deze optie niet aanvinkt, dan kan je in de command line tool er geen gebruik van kan maken. Om dat op te lossen moet je heel wat manueel werk verrichten, vergeet dit dus zeker niet 

Hoe weet je of Git geïnstalleerd is? Open een command line interface/terminal, typ `git` en druk op enter. Als je alle functies van Git te zien krijgt, is Git goed geïnstalleerd.

### Ik krijg 'git wordt niet herkend als interne of externe opdracht, programma of batchbestand'

Als je de installatie hebt doorlopen, moet je eerst een nieuwe command line interface opstarten. Als je een nieuwe instantie van de cli hebt opgestart en je hebt 'git' getypt, maar zonder resultaat, dan ben je waarschijnlijk vergeten Git toe te voegen aan je PATH-variabele.

Je kan dit manueel doen door naar Start > computer (rechtermuisklik) > eigenschappen > geavanceerde instellingen > Geavanceerd (Tabblad) > omgevingsvariabelen > Systeemvariabelen > Path (selecteren) > Bewerken > Waarde van variabele

Als je daar bent, mag je niets verwijderen, maar voeg je een ';' toe op het einde van deze lijn. Daarna ga je op zoek naar de plaats waar Git is geïnstalleerd en de map waar git.exe zich bevindt. Normaalgezien is dat C:\Program Files (x86)\Git\cmd

Copy-paste deze directory (C:\Program Files (x86)\Git\cmd) en plak ze achteraan de lijn 'Waarde van variabele'. Druk op ok, start een nieuwe instantie van de CLI en typ daarna `git`. Normaalgezien zou je nu uitleg moeten krijgen over hoe je Git kan gebruiken.

## Git project aanmaken

Alles gebeurt via de CLI

Navigeer naar de folder waarin je een nieuw project wil starten en typ

```
git init
```

Dit maakt een nieuwe repository aan. 

Een repository is de naam voor een project en betekent letterlijk 'bewaarplaats'. Wanneer je kijkt naar de folder, zal je zien dat er een verborgen '.git' map is aangemaakt. Hierin staat alle informatie die Git nodig heeft. Verwijder je deze folder, dan verwijder je alle informatie die Git over het project heeft aangemaakt. Doe dit dus niet, tenzij je Git voor dit project wil verwijderen (maar waarom zou je dat doen?)


```
git status
```

Hiermee kan je nagaan welke files zijn toegevoegd aan de repository en dewelke zijn gewijzigd.

Onder 'untracked files' vind je de bestanden terug die nog niet door Git worden gemonitord. Wanneer je een nieuwe file aanmaakt, moet je aan de Git repository toevoegen. Doe je dit niet, kan er van die file geen versiebeheer worden aangemaakt.

### wijzigingen monitoren (git add)

Wanneer een nieuwe file is aangemaakt of wanneer je een wijziging aan een file maakt, moet je Git hiervan op de hoogte brengen. Het versiebeheer gebeurt dus niet automatisch.

```
git add path/to/file.txt
```

Door `add` uit te voeren, breng je Git op de hoogte dat de files gewijzigd zijn. Het laatste argument is de plaats waar de gewijzigde file zich bevindt. Meestal verander je meerdere files tegelijk en wil je alle changes opnemen. Dan kan je best de `.` wildcard gebruiken. Deze staat voor alle files in alle directories in de Git repository. 

```
git add .
```

### bepaalde files of folders negeren (.gitignore)

Soms wil je niet dat bepaalde files gemonitord worden, zoals files die te maken hebben met je IDE. Daarvoor kan je een .gitignore file maken die je in de root-folder van je Git repository plaatst. In deze file kan je door middel van Regular Expressions files toevoegen die geen onderdeel zijn van het Git project.

```
# User-specific files
*.suo

# Build results
[Dd]ebug/
```

Op [Github Gitignore](https://github.com/github/gitignore) vind je een hele reeks aan voorgemaakte .gitignores die van toepassing zijn voor IDE's. 

### wijzigingen toevoegen aan de huidige branch (git commit)

Wanneer je klaar bent met het toevoegen van een bepaalde functionaliteit, moet je een commit uitvoeren. Een commit stelt Git dan op de hoogte dat de huidig versie de laatste nieuwe versie is van de branch is (later hierover meer). 

```
git commit -m "Add upvote functionality"
```

De `-m" flag staat voor message, hiermee voeg je een boodschap toe aan je commit. Voeg altijd een boodschap toe aan je commit, want dit is de enige manier om een beschrijving aan je wijzigingen toe te voegen. 

Een goede commit message begint met een werkwoord gevolgd door een onderwerp en bevat meestal maar enkele woorden. 

Een goede raad: "Commit early, commit often". Daarmee wordt bedoeld dat je niet moet wachten tot je een werkende versie hebt van je applicatie vooraleer een commit uit te uitvoeren. En hoe meer commits, hoe beter. Dit zorgt ervoor dat wanneer er iets niet meer werkt, je de branch makkelijk kan terugrollen naar een vorige commit. Zo zal je applicatie niet alleen terug werken, je zal ook makkelijker je fout kunnen localiseren door te kijken naar wat er gewijzigd is.

In het begin is het even wennen, maar een goede commit history kan je heel wat kopzorgen besparen. Commit early, commit often!

### wijzigingen bekijken 

Dit is iets waar de CLI wat in  tekort schiet. De GUIs zoals ScourceTree zijn heel goed in het in beeld brengen van de verschillende versies en de verschillen tussen de verschillende versies. De GUIs zijn dus zeker de moeite om eens te bekijken. Maar, met de CLI gaat het ook:

```
git diff
```

Hiermee worden alle files vergeleken met de versie van de laatste commit. Je kan dit dus enkel uitvoeren tussen het moment dat je een wijziging hebt gemaakt en het uitvoeren van de commit.

```
git log
```

Deze command brengt je volledige commit history in kaart. Je ziet bij elke commit ook een hashkey staan. Dat is het unieke identificatienummer van je commit. Je kan makkelijk tussen verschillende commits navigeren door de volgende command:

```
git checkout hashkey
```
Waarbij je hashkey vervangt door de key van de commit dit je wil bekijken.

### wijzigingen ongedaan maken

Soms kan het zijn dat je wijzigingen wil terugrollen naar de laatste commit. Dat kan makkelijk door

```
git checkout -- .
```

Let op, alle wijzigingen die je hebt uitgevoerd ben je dan permanent kwijt. Dus, commit early, commit often.

## Git branches



## Een bestaand lokaal Git-project koppelen aan een online repository

## Git een online repository laten binnenhalen (clonen)

## Nuttige Git commands

- Url van origin wijzigen
- Naam van de branch wijzigen

