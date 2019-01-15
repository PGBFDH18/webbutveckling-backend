# Fia konsol applikation

Allt ni gör skall göras i ert GitHub repo (båda kod och dokumentation), som ligger på ert Team. Ni skall använda en ["commit tidigt och ofta"](https://blog.codinghorror.com/check-in-early-check-in-often/) ([1](https://sethrobertson.github.io/GitBestPractices/)) strategi, såklart bör ni endast commita kod som kan kompileras.
Ert repositiory ska vara konfigurerat så att det enda sätt att få in kod i master branchen är via pull requests.

# Programmering
I detta projekt ska ni implementera ett fia spel (Ludo på engelska). Spelet ska vara en .net core konsol applikation.

Kod ska ligga i mappen **src**, varje team får enbart ha en kodbas!!

All logik ska göras i ett separat kod bibliotek.

## Grundtanken 
Det ska vara möjligt att spela spelet för mellan två och fyra spelare.

## Spelmotor (GameEngine)
Spelmotorn styra alla regler i spelet och kollar t.ex. om en spelpjäs får flyttas, om en spelar har vunnit, den initiala uppställning av alla spelpjäser på brädet, vilken spelar som är den nästa, hur en tärning ska bete sig, etc.

Implementera spelmotorn i ett separat klass bibliotek.

En instans av spelmotorn innehåller staten av ett helt spel, det skall vara möjligt att initialisera spelet med en given state, t.ek. om ska kunna spara och inläsa ett spel.

# Dokumentation
Skriv [user stories](https://www.mountaingoatsoftware.com/agile/user-stories) (i docs mappen), och starta inte koda något innan in har skrivet minst 3 user stories, men helst så det täcker hela fia spelet, men se hela tiden till att lägga till fler user stories.

Om ni använder någon externa källor (båda kod och annat) ange dom i dokumentationen.

Dokumentation ska skrivas med markdown (.md), ni väljer själv om ni vill skriva på svenska eller engelska, markdown filerna placeras i **docs** mappen.

# Betygsättning
Detta projekt är **inte** betygsgrundande.

Projektet är ment som ett test projekt på att komma igång med detta kurs, och en introduktion till fia.

## Extra utmaning

För dom som gärna vill ha litet extra utmaning kan man börja titta på att:

* implementationen skall följa SOLID principerna, så långt det går
* Ett enhetstest (Unit Test) projekt skall skåpas, och logiken i spelet ska testas med enhetstestar.