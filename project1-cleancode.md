###### Exempler från projekt 1 - konsol Fia

``` csharp
        private static void Run()
        {
            Console.ForegroundColor = (ConsoleColor)Enum.Parse(typeof(ConsoleColor), S.GetCurrentPlayer());
            Console.WriteLine("");
            Console.WriteLine("What do you wanna do?");
            Console.WriteLine("1: See who's turn it is.");
            Console.WriteLine("2: Look at current playingfield.");
            Console.WriteLine("3: Roll dice.");
```
Run? Run what?

``` csharp
        private static void SetNumberOfPlayers()
        {
            Console.ForegroundColor = ConsoleColor.Red;
            while (numberOfPlayers < 2 || numberOfPlayers > 4)
            {
                Console.WriteLine("Input numbers of players:");
```
- Där händer något med ForegroundColor
- Någon inläsning från konsol

``` csharp
        public List<string> PlayerRoll()
        {
            string temp;
            List<string> alternative = new List<string>();
```
Where is the player rolling?

``` csharp
        public int Alternatives(int roll)
        {
```
Alternatives to what? Since it's the Session-class, is it the alternative sessions?

``` csharp
        private string[] PieceFromNest(int pieceNr)
        {
```
Vad kommer att hända?



##### 