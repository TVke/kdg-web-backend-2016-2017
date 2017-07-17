# GIT crash course

- De onderstaande commands zijn voor de [Git-CLI](https://git-scm.com/) in samenwerking met [GitHub](https://www.github.com). Je hebt dus een beetje kennis nodig van de command line tool.
- Je kan gebruik maken van Git-GUI's ([GitGIU](https://git-scm.com/docs/git-gui), [SourceTree](https://www.sourcetreeapp.com/)), maar het is beter om eerst te weten wat de basiscommando's zijn vooraleer je je hier aan waagt.
- Enkele interessante Git-tutorials:
  - [Try Git - interactive tutorial](https://try.github.io)
  - [The beginner's guide to contributing to a GitHub project](https://akrabat.com/the-beginners-guide-to-contributing-to-a-github-project/)
  

## Wat is Git?

Een gedistribueerd versiebeheersysteem. 

Versiebeheer laat je toe om verschillende versies van een applicatie bij te houden zodat je makkelijk naar een vorige versie kan teruggrijpen. Het staat je ook toe om met een team aan één applicatie te werken, zonder dat je daarbij elkaars werk overschrijft. 

Gedistribueerd betekent dat iedereen een kopie heeft van de originele applicatie, in tegenstelling met gecentraliseerd versiebeheersysteem (CVS), waarbij iedereen dezelfde "master"-versie heeft. Gecentraliseerd versiebeheer heeft enorm veel nadelen ([Linus Torvalds, de uitvinder van het distribueerde systeem, legt uit waarom](https://www.youtube.com/watch?v=4XpnKHJAok8)) en zou dus niet meer mogen gebruikt worden.

Git is voornamelijk bedoeld voor bestanden die tekst bevatten en niet voor gecompilede bestanden (binary files) zoals afbeeldingen, pdf's, exe's, ... (hoewel het wel mogelijk is)

Let op, Git en Github zijn niet hetzelfde. Git is een versiebeheersysteem, terwijl GitHub een online platform is om repositories op te hosten, net zoals BitBucket er een is. Ze staan dus volledig los van elkaar.

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

De `-m` flag staat voor message, hiermee voeg je een boodschap toe aan je commit. Voeg altijd een boodschap toe aan je commit. Dit is makkelijk omdat je dan in een oogopslag weet welke wijzigingen je in die commit hebt uitgevoerd zonder dat je naar de code moet kijken.

Een goede commit message begint met een werkwoord in de tegenwoordige zijd gevolgd door een onderwerp. Hou de commit message zo bondig mogelijk. 

Een goede raad: "Commit early, commit often". Daarmee wordt bedoeld dat je niet moet wachten tot je een werkende versie hebt van je applicatie vooraleer een commit uit te uitvoeren. En hoe meer commits, hoe beter. Dit zorgt ervoor dat wanneer er iets niet meer werkt, je de branch makkelijk kan terugrollen naar een vorige commit. Zo zal je applicatie niet alleen terug werken, je zal ook makkelijker je fout kunnen localiseren door te kijken naar wat er gewijzigd is.

In het begin is het even wennen, maar een goede commit history kan je heel wat kopzorgen besparen. Commit early, commit often!

### wijzigingen bekijken 

Dit is iets waar de CLI wat in  tekort schiet. De GUIs zoals ScourceTree zijn heel goed in het visualiseren van de verschillende versies. De GUIs zijn dus zeker de moeite om eens te bekijken. Maar, met de CLI gaat het ook:

```
git diff
```

Hiermee worden alle files vergeleken met de versie van de laatste commit.Je kan dit dus enkel uitvoeren tussen het moment dat je een wijziging hebt gemaakt en het uitvoeren van de commit.

Deze command brengt je volledige commit history in kaart:

```
git log
```

Je ziet bij elke commit ook een hashkey staan. Dat is het unieke identificatienummer van je commit. Je kan makkelijk tussen verschillende commits navigeren door de volgende command:

```
git checkout hashkey
```
Waarbij je hashkey vervangt door de key van de commit dit je wil bekijken. Let wel op, wanneer je een commit wil bekijken door middel van checkout, wordt er automatisch een nieuwe branch gemaakt.

### wijzigingen ongedaan maken

Soms kan het zijn dat je wijzigingen wil terugrollen naar de laatste commit. Dat kan makkelijk door

```
git checkout -- .
```

Let op, alle wijzigingen die je hebt uitgevoerd ben je dan permanent kwijt. Dus, commit early, commit often.

## Git branches

Een branch is een finale versie van je applicatie. Wanneer je een commit uitvoert, wordt deze dus toegevoegd aan de branch waar je op dat moment in zit te werken.

```
git branch
```

Dit somt alle branches op die de repository kent. Wanneer je een nieuw project start, werk je altijd op de master branch.

Maar wat is een branch precies? Stel, je wil een update aan je applicatie uitvoeren, dan is het niet de bedoeling dat je in de master branch je commits gaat uitvoeren, maar dat je een nieuwe branch aanmaakt. Een nieuwe branch aanmaken betekent dat je een exacte kopie maakt van de branch waarin je dat moment zit te werken. Dit doe je zo

```
git checkout -b nameOfNewBranch
```

De -b flag staat voor de branch naam. In plaats van nameOfNewBranch schrijf je in één woord aan welke wijziging je zal werken, bv. downvoteFunctionality. Vaak worden er ook versienummers gebruikt als branchnaam, maar dan wordt het moeilijker om te achterhalen waar er op dat moment in die branch aan wordt gewerkt. 

Wanneer je deze command uitvoert, zal je je ook automatisch in de net aangemaakte branch bevinden. Verder doe je je commits zoals je die gewoon bent. 

Een goede gewoonte is om nooit in de master branch te werken. Dat wordt al heel snel duidelijk wanneer je bijvoorbeeld een critical bug moet fixen maar al aan een nieuwe versie van de applicatie bezig bent (in een nieuwe branch, uiteraard).

Als je een branch een nieuwe naam wil geven, dan kan je de volgende command uitvoeren:

```
git checkout -m oudeBranchName nieuweBranchName
```

De "-m" flag staat voor move (of mv) wat in CLI-commands gebruikt wordt om een bestand te hernoemen (verplaatsen naar een locatie met een andere naam). 

Om een fout te fixen die zich in de master branch bevindt kan je dan makkelijk je werk voor de update even opzij zetten. Eerst doe je een commit van je huidige werk, anders verlies je alles tot aan de laatste commit die je hebt uitgevoerd. Daarna ga je naar de master branch door

```
git checkout master
```

Je maakt een nieuwe branch van de master, bv. `git checkout -b bugFix`, je fixt de bug en voert de commits uit zoals je die gewoon bent. 

Het is niet zo dat wijzigingen in een kopie van een branch, ook in de originele branch plaatsvinden. Je moet de wijzigingen in de nieuwe branch mergen met de branch waarvan je de kopie hebt genomen. 

Wanneer je klaar bent, kan je de bugFix branch met de master mergen, zodat de officiële versie van je applicatie die zich in de master bevindt, ook de wijzigingen uit de bugFix zal ontvangen. Navigeer daarvoor eerst naar de branch die de bugFix moet ontvangen en voer daarin de volgende command uit

```
git merge bugFix
```

Ziezo, een bug gefixt. Het voordeel van deze werkwijze is dat je nu weer makkelijk naar de te updaten branch kan switchen, zonder dat je werk verloren is gegaan of dat je hebt moeten wachten tot deze update afgewerkt was om aan de bug te beginnen.

Waar je wel rekening mee moet houden is dat de master nu 'ahead' is op de branch waarin je je updates aan het uitvoeren bent. Dit wil zeggen dat er in de master wijzigingen hebben plaatsgevonden die niet in de huidige branch zitten. Dat is makkelijk op te lossen door de master branch te mergen in de branch die 'behind' is.

### Merge conflict

Meestal gebeurt het mergen zonder problemen, maar af en toe gebeurt het dat er een merge conflict ontstaat. 

Een merge conflict gebeurt wanneer je een branch wil mergen, maar dat de branch waarvan je de kopie hebt gemaakt wijzigingen bevat die niet in de gekopieerde versie van de branch zitten. Git zal de files dan niet automatisch mergen, maar zal op de plaats waar het merge conflict plaatsvind, beide stukjes code in de volgende syntax weergeven

```
<<<<<<< HEAD
originele code uit master branch
=======
nieuwe code uit kopie van master branch
>>>>>>>
```

Je zal dus zelf moeten beslissen welk stukje code je wil overhouden en welk stukje verwijderd kan worden. Verwijder ook de syntax die Git heeft toegevoegd om het merge conflict aan te duiden, anders zal Git niet herkennen dat je het merge conflict hebt opgelost.

## Git een online repository laten binnenhalen (clonen)

Vaak wil je bestaande repositories op Github lokaal binnenhalen zodat je er zelf mee aan de slag kan. Dat kan heel makkelijk. 

Ga op zoek naar de url waar het te clonen project zich bevindt. Dit is meestal ergens onder een "clone or download" functionaliteit. Let op, de url moet op eindigen met de bestandsextensie .git, zoals bv. https://github.com/jquery/jquery.git

Open je CLI en navigeer naar de map waar de te clonen repository moet komen en voer daarna deze command uit:

```
git clone https://github.com/jquery/jquery.git jquery
```

Het woord na de repository-url is de naam van de map waarin de repository moet komen. Laat je dit weg, dan wordt er geen nieuw map aangemaakt en zal de repo in de huidige map worden gekopiëerd. 

Dit clonen hoef je maar één keer te doen. Van zodra je een online repo hebt gecloned, kan je makkelijk de laatste nieuwe versie binnenhalen door naar de map te navigeren waarin de geclonede repo zich bevindt. In het bovenstaande voorbeeld is dat dus in de map /jquery en niet in de bovenliggende map. Voer daarna de volgende command uit:

```
git pull origin master
```

In het volgende hoofdstuk meer over deze command.

## Een bestaand lokaal Git-project koppelen aan een online repository

Je hebt een eigen project klaar en wil dit delen met de rest van de wereld. Dat kan via de services van Github of BitBucket. Schrijf je in op een van deze sites. Op je profiel maak je een nieuwe repository aan en je geeft dit de naam van je nog online te zetten project. Ga op zoek naar de URL waar deze online repo zich bevindt (remote) en hou deze even bij.

Open je CLI en navigeer naar de map waar je repo zich bevindt. Voer de volgende command uit: 

```
git remote add origin https://github.com/username/locatie-van-de-remote.git
```

Zorg er zeker voor dat de URL die je gebruikt eindigt op de .git extensie. De "remote add" wordt gebruikt om een locatie toe te voegen waar je een online versie van de repo kan vinden. "origin" is de alias (variabelenaam) van deze remote. Je kan deze dus eender welke naam geven, maar doorgaans wordt origin gebruikt om een remote aan te duiden.

Je kan dus meerdere online locaties toevoegen, zolang de naam van de alias nog niet gebruikt is. Dit kan je doen als je een project zowel naar GitHub als naar BitBucket wil uploaden (bv. originGH, originBB).

Als je merkt dat je een fout hebt gemaakt in de URL (.git vergeten), of je wil de URL van de origin van locatie wijzigen, dan kan dat met de volgende command:

```
git remote set-url origin https://github.com/username/nieuwe-locatie-van-de-remote.git
```

Waarbij "origin" de alias is van de remote die je wil wijzigen. Bevestig daarna even of de wijziging goed is doorgevoerd door middel van deze command:

```
git remote -v
```

Hierdoor krijg je alle remotes met bijhorende URL te zien. De "-v" flag staat voor verbose en toont de URL van de remote. 

Je hebt enkel nog maar aan Git verteld wáár die remote zich bevindt, maar het project zelf staat nog niet online. Dat doen we nu.

Soms kan het zijn dat er in de online repository die je net hebt aangemaakt, bestanden zitten die niet in de lokale repository zitten. Deze moet je eerst ook lokaal hebben staan, anders zijn de lokale en remote repo niet in sync. Voer daarom eerst de volgende command uit:

```
git pull origin master
```

Dit haalt alle online wijzigingen binnen. "origin" staat voor de alias die verwijst naar de URL van de remote en "master" is de naam van de online branch die in de huidige lokale branch gemerged moet worden.

```
git push -u origin master
```

Net zoals bij de `pull` command staat "origin" voor de alias die verwijst naar de URL van de remote en is het "master" argument de naam van de online branch waaraan de wijzigingen toegevoegd moeten worden. Deze command geeft je meestal de meeste voldoening, want het betekent dat er een bepaald deel van de applicatie is afgewerkt en klaar is om online te zetten.

De "-u" flag staat voor "upstream", maar dat is een [redelijk complex verhaal](http://stackoverflow.com/questions/33503080/learning-git-tracking-vs-setting-upstream-u-for-remotes) dat interessant is als achtergrondinformatie, maar niet essentiëel is om met Git aan de slag te kunnen.

