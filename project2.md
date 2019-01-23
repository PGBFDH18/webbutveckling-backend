# Fia Web API

Detta projekt bygger vidre på projektet Fia Konsol Applikation, ni har inte direkt behov av själva konsol applikationen men eran game engine, och istället för en konsol applikation som gör det möjligt att spela Fia ska ni bygga ett REST web api som använder eran game engine till att göra det möjligt att spela Fia via ett web api.

Allt ni gör skall göras i ert GitHub repo (båda kod och dokumentation), som ligger på ert Team. Ni skall använda en ["commit tidigt och ofta"](https://blog.codinghorror.com/check-in-early-check-in-often/) ([1](https://sethrobertson.github.io/GitBestPractices/)) strategi, såklart bör ni endast commita kod som kan kompileras.
Ert repositiory ska vara konfigurerat så att det enda sätt att få in kod i master branchen är via pull requests (detta göras av underviseren), detta betyder att ni inte kan jobba direkt i master men får skåpa en eller fler nya branches som ni jobber i ([feature branches](https://paulhammant.com/2013/04/05/what-is-trunk-based-development/)).

# Dokumentation

Se till att skriv och uppdatera eran [user stories](https://www.mountaingoatsoftware.com/agile/user-stories) (i */docs* mappen), så att dom passer med ert Web Api. Om ni använder någon externa källor (båda kod och annat) ange dom i dokumentationen.

Evt dokumentation kan skrivas med markdown (.md) eller ett annat format som ni känner er bekväma med (.txt, ~~.docx~~, .html, ~~.pdf~~ etc), ni väljer själv om ni vill skriva på svenska eller engelska, enda krav är att filerna placeras i */docs* mappen.

## OpenAPI beskriving av API

Innan ni går på gång med att implementera koden till Web APIet ska ni skriva en OpenAPI dokumentaion av APIet, se till att få med så många detaljer som möjligt, och gära exempler på vad APIet retunera. Denna OpenAPI fil ska ni placera i */docs* mappen.
Dock är OpenAPI en stor specifikation, och det är orealistisk innom projekts tidsram att få med alla detaljer i OpenAPI, så det viktigaste är att ni beskriver vilka paths och metoder som är till tillgängliga på dissa paths.

Ett exemplet kunne vara att kalla den */docs/ludowebapi.yml*.

Ni kan använda SwaggerHub till att skriva OpenAPI filen i, där finns även i SwaggerHub en [Github integration](https://app.swaggerhub.com/help/integrations/github-sync) som gör det möjligt att ha eran OpenApi definations fil i Github.

Alternativt kan ni Visual Studio Code till att skriva filen med, och lägg till extentions för OpenAPI som underlätter jobbat.

# Programmering
I detta projekt ska ni implementera ett Web API till ert Fia spel (Ludo på engelska). Spelet ska vara en .NET Core Web API.

Kod ska ligga i mappen **src**, varje team får enbart ha **en kodbas**. Där finns i detta repository en *gitignore*-fil som passer till Visual Studio, i **src**-mappen finns även en tom solution, denna kan ni använda till att lägga till eran projekt (Web API och GameEngine)

Önsker ni inte att använda eran egen game engine, kan ni här hitta en väldigt basic ludo game engine: [LudoGameEngine](https://github.com/skjohansen/LudoGameEngine)

Det rekomeneras att ni kopiere in game enginen i eran **src**-mapp.

## Grundtanken 
Det ska vara möjligt att spela spelet för mellan två och fyra "spelare".

Det ska bara möjligt att starta fler samtidiga spel, på servern. Varje spel ska av sitt eget unika ID, ett spel ska inta dö.

# Extra: Byggen av API

Konfigurer byggen av eran API i Azure DevOps

# Betygsättning
Detta projekt är betygsgrundande.

## Pull request
Ni kan göra så många branches baseret på *master* som ni önsker. När projektet är slut är det innehållet av master på **GitHub** som räcknas, så ni behöver att göra minst ett pull request från eran branch(s) till *master* under projektet med reviewers från ett annat team. Varje branch får två reviews teams upplagt på ert repo av underviseren.

## För G
* En (och endast en) Visual Studio solution placerat i mappen Src
* Solutionen ska beså av minst två projekt:
  * Ett ASP.NET Core WebApi
  * Class Library med en game engine

* Koden kompilera och det går att köra projektet lokalt
* All logik som rör spelet, även kast av tärning, är placerat i spelmotorn
* Dokumentation av hur APIet är upplagt, en OpenAPI fil (yaml) ør rekomenderat
* Som api-användere ska gå att skåpa ett eller fler spel
* Som api-användere ska gå att spela ett eksisterende spel

## För VG (G + minst 3 för VG)
* CI i Azure Devops (dokumentation för detta läggs i Docs mappen)
* Automatiska test av API som kan köras lokalt
* PostMan testar, det är möjligt i Postman att konfigurera Team Workspaces som man kan dele api requests med varandra, man även importera en OpenAPI fil. 
* En applikation som gör det möjligt att spela Fia via Web APIet (detta kunna vara en konsol applikation)
* Lagring av data, spel data lagres äntligen disk eller i någon form av databas
* **MORE TO COME, kom med förslag**

# Hints
## API 
Ett **förslag** på resources och hur olika metoder påverkar dom

|                                   | GET<br />read                                                | POST<br />create                    | PUT<br />update                   | DELETE<br />delete |
| --------------------------------- | ------------------------------------------------------------ | ----------------------------------- | --------------------------------- | ------------------ |
| /ludo                             | Lista av fia spel                                            | Skåpa ett nytt spel                 | N/A                               | N/A                |
| /ludo/{gameId}                    | Detaljeret information om spelet, som vart alla pjäser finns | N/A                                 | Ändra placering på en pjäs        | Ta bort ett spel   |
| /ludo/{gameId}/players            | List med alla spelera i spelet                               | Lägg till en ny spelere till spelet | N/A                               | N/A                |
| /ludo/{gameId}/players/{playerId} | Detajeret information om speleren                            | N/A                                 | Ändra namn eller färg på speleren | Ta bort speleren   |

Beskrivet med OpenAPI:
```yaml
openapi: 3.0.0
info:
  title: Ludo Api
paths:
  /ludo:
    get:
	  description: Lista av fia spel   
	post:
	  description: Skåpa ett nytt spel
  /ludo/{gameId}:
    get:
	  description: Detaljeret information om spelet, som vart alla pjäser finns
```
## Kom igång
1. Börja med att försöka att skissa APIet på något sätt, och spara resultatet i docs-mappen
1. Öppna solution-filen som ligger i src-mappen, och lägg till ett [nytt WebAPI](https://www.c-sharpcorner.com/article/quick-start-to-create-restful-web-api-in-asp-net-core/)
1. Lägg till ett existerande GameEngine projekt
1. Lägg till controllers som matcher dom resurser (paths) som ni har beskrivit i eran dokumentation (från punkt 1)
1. Lägga till en referens till LudoEngine i ert  Web API
1. Börja att implementera eran controllere, så att dom använder GameEngine till att göra operationer i spelet
1. Testa löppande APIet med ett verktyg som Postman
1. Få till dependency injection (se Hints)

## Anrop APIet från en annan applikation

Exempel på hur du kan använda och testa ett REST Web API med en konsol applikation (eller annat C# kod)
Nuget paket: [RESTSharp](https://www.nuget.org/packages/RestSharp/) ([Projekt på Github](https://github.com/restsharp/RestSharp))

```csharp
// Retrive the name of a specific Ludo game using the REST API
var client = new RestClient("http://ludoapi.com");

var request = new RestRequest("ludo/{id}", Method.GET);
request.AddUrlSegment("id", "123"); // replaces matching token in request.Resource
RestResponse<LudoGame> ludoGameResponse = client.Execute<LudoGame>(request);
var gameName = ludoGameResponse.Data.GameName;

```

Kolla evt denna artikel med olika tillgångar till hur man kan kommunicera med ett REST API: [A Few Great Ways to Consume RESTful API in C#](https://code-maze.com/different-ways-consume-restful-api-csharp/)

## Dependency injection i ASP.NET core 

För att få till [Dependency injection](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.2) med ASP.NET core kan man i grov drag göra något som detta:

In the startup class use the build in DI
```csharp
public class Startup
{
	// something
	public void ConfigureServices(IServiceCollection services)
	{
		// something MVC
		services.AddScoped<GameEngine.IGameEngine, GameEngine.GameEngine>();
		services.AddScoped<GameEngine.IGameRetriver, GameEngine.FileGames>();
	}
	// something
}
```

GameEngine:
```csharp
namespace GameEngine
{
    public interface IGameEngine
    {
        List<Game> LoadGames();
    }
	
	public interface IGameRetriver
    {
        List<Game> Query(string v);
    }
	
	public class GameEngine : IGameEngine{
        private IGameRetriver _retriver;

        public GameEngine(IGameRetriver r){
             _retriver = r;
        }

        public List<Game> LoadGames(){
            return _retriver.Query("select whatever");
        }
    }
}
```

Controller:
```csharp
public class ValuesController : ControllerBase
{
	
	private Ge.GameEngine _game;
	public ValuesController(Ge.GameEngine ge){
		_game = ge;
	}

	// GET api/values
	[HttpGet]
	public ActionResult<IEnumerable<string>> Get()
	{
		return Ok(_games.game.LoadGames().ToArray());
	}

}
```


## Postman

Postman är ett program som kan användas till att tillgå och testa ett Web API, man kan tänka på Postman som en webläsere för WebAPIer (ursprungligt var Postman en extention till Chrome).