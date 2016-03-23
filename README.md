# American_Checkers_Federation_Data

The reason for cleaning this data was to use it as an opening moves database in a checkers AI that I wrote as a school project.  The 60 years of checkers games played at the tournament level should contain the most popular opening moves and their variations.

#Data Source and Format

The file acf_download_1257729234.pnd was download from the American Checkers Federations website (http://www.usacheckers.com/).  It contains over nine thousand checkers games played at tournaments hosted by the ACF since the early fifties.  The data required some 
modifications and cleaning in order to get it into a usable format.  The result of which is contained in the file 
FormatedCheckersGames.tab.  

FormatedCheckersGames.tab contains seven different tab seperated values:  
1) Unique game id (not included in original file)  
2) Event name and sometimes a game number   
3) Black player name  
4) Red player name  
5) Result of game(1-0 black, 0-1 red win, 1/2-1/2 tie)  
6) Date game was played  
7) List of game plays seperated by spaces with the last value being the game result again. (BE WARNED: Some jumps are   listed as 27-18 instead of 27x18.)  

#Game Basics for Data

Black always goes first and starts at the top of the board.  The board notation is listed below:  
  
x  1 x 2  x 3  x 4  
5  x 6 x  7 x  8 x  
x  9 x 10 x 11 x 12  
13 x 14 x 15 x 16 x  
x 17 x 18 x 19 x 20  
21 x 22 x 23 x 24 x  
x 25 x 26 x 27 x 28  
29 x 30 x 31 x 32 x  

A move from 9 to 14 would represented by 9-14.  
A jump from 9 to 18, jumping a piece at 14, would be represented by 9-18.  

Generating each state of the board for every turn requires re-executing each move as listed.

#Using the Data

In order to use the data it was placed in an sqlite file, GameTable.db, that contained the number of black wins, red wins, draws, game path, next play and current board state(an inverted state also exsisted incase red went first).  The best play was determined by the highest win and draw percents.

In practice, the database only really proved to be useful for the first ten plays or so.  In many cases, if the opponent does not know any counter to opening plays the game can deviate from any played games by the second move.
