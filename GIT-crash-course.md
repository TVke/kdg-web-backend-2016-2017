# GIT crash course

- De onderstaande commands zijn voor de [Git-CLI](https://git-scm.com/) in samenwerking met [GitHub](https://www.github.com). Je hebt dus een beetje kennis nodig van de command line tool.
- Je kan gebruik maken van Git-Gui's ([GitGIU](https://git-scm.com/docs/git-gui), [SourceTree](https://www.sourcetreeapp.com/)), maar het is beter om eerst te weten wat de basiscommando's zijn vooraleer je je hier aan waagt.
- Enkele interessante Git-tutorials:
  - [Try Git - interactive tutorial](https://try.github.io)
  - [The beginner's guide to contributing to a GitHub project](https://akrabat.com/the-beginners-guide-to-contributing-to-a-github-project/)
  

## Wat is Git?

Een gedistribueerd versiebeheersysteem. 

Versiebeheer laat je toe om verschillende versies van een applicatie bij te houden, zodat je makkelijk naar een vorige versie kan teruggrijpen. Niet alleen dat, het laat je ook toe om met een team aan één applicatie te werken, zonder dat je daarbij moet letten op het overschrijven van elkaars werk. 

Gedistribueerd betekent dat iedereen een kopie heeft van de originele applicatie, in tegenstelling met gecentraliseerd versiebeheersysteem, waarbij iedereen dezelfde "master"-versie heeft. Gecentraliseerd versiebeheer heeft enorm veel nadelen ([Linus Torvalds, de uitvinder van het distribueerde systeem, legt uit waarom](https://www.youtube.com/watch?v=4XpnKHJAok8))en zou dus niet meer mogen gebruikt worden.

## Git installeren

Voor Linux en Mac gebruikers is het makkelijk, daar is Git standaard geïnstalleerd. Windows-gebruikers moeten dit expliciet installeren. Surf naar [Git-SCM](https://git-scm.com/) en download de juiste versie.

Verder moet je er zeker van zijn dat je bij de installatie Git toevoegt aan je PATH-variabele. Als je deze optie niet aanvinkt, dan kan je in de command line tool er geen gebruik van kan maken. Om dat op te lossen moet je heel wat manueel werk verrichten, vergeet dit dus zeker niet 

Hoe weet je of Git geïnstalleerd is? Open een command line interface/terminal, typ ´git´ en druk op enter. Als je alle functies van Git te zien krijgt, is Git goed geïnstalleerd.

### Ik krijg 'git wordt niet herkend als interne of externe opdracht, programma of batchbestand'

Als je de installatie hebt doorlopen, moet je eerst een nieuwe command line interface opstarten. Als je een nieuwe instantie van de cli hebt opgestart en je hebt 'git' getypt, maar zonder resultaat, dan ben je waarschijnlijk vergeten Git toe te voegen aan je PATH-variabele.

Je kan dit manueel doen door naar Start > computer (rechtermuisklik) > eigenschappen > geavanceerde instellingen > Geavanceerd (Tabblad) > omgevingsvariabelen > Systeemvariabelen > Path (selecteren) > Bewerken > Waarde van variabele

Als je daar bent, mag je niets verwijderen, maar voeg je een ';' toe op het einde van deze lijn. Daarna ga je op zoek naar de plaats waar Git is geïnstalleerd en de map waar git.exe zich bevindt. Normaalgezien is dat C:\Program Files (x86)\Git\cmd

Copy-paste deze directory (C:\Program Files (x86)\Git\cmd) en plak ze achteraan de lijn 'Waarde van variabele'. Druk op ok, start een nieuwe instantie van de CLI en typ daarna ´git´. Normaalgezien zou je nu uitleg moeten krijgen over hoe je Git kan gebruiken.

## Git project aanmaken

Alles gebeurt via de CLI

Navigeer naar de folder waarin je een nieuw project wil starten en typ

´´´´
git init
´´´´

Dit maakt een nieuwe repository aan. 

Een repository is de naam voor een project en betekent letterlijk 'bewaarplaats'. Wanneer je kijkt naar de folder, zal je zien dat er een verborgen '.git' map is aangemaakt. Hierin staat alle informatie die Git nodig heeft. Verwijder je deze folder, dan verwijder je alle informatie die Git over het project heeft aangemaakt. Doe dit dus niet, tenzij je Git voor dit project wil verwijderen (eh... waarom?)

### wijzigingen monitoren (git add)

### wijzigingen toevoegen aan de huidige branch (git commit)

### bepaalde files of folders negeren (.gitignore)

## Git branches



## Een bestaand lokaal Git-project koppelen aan een online repository

## Git een online repository laten binnenhalen (clonen)

## Nuttige Git commands

- Url van origin wijzigen
- Naam van de branch wijzigen

