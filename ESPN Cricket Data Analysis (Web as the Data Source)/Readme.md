# In this project we will do -
1️⃣ Web Scrapping in Power BI<br>
2️⃣ Use publicly available ESPN cricket data online<br>
3️⃣ We are interested only in ODIs

## Getting the data by:
- Google search bar
- Search "espn cricinfo statsguru"
- Select "ODI"
- Select "Batting"
- Team: India
- Opposition: South Africa
- Home or away: Select Non
- Submit query

## Power BI desktop page set up. Go to
- File
- Options & settings
- Options
- Data load
- Type Detection
- Select option 3: "Never detect column types and headers for unstructured sources."

## For Web as the Data Source (Web Scrapping), select
- Get Data
- Web
- URL
- Stay "Anonymous"
- Click Ok

# Method 1 - Incase of Multiple tables 
- **Select table - "Overal Figures"**
- Choose "Transform"

## In Power Query editor
- Home
- Use first row as headers
- Remove last column (Unnecessary column)
- Close & Apply
 
# Method 2 (Better way for data cleaning) - Incase of Multiple table
- **Add table using examples**
- Copy the first row from the original table
- Copy the second row from the original table
- Now Power BI auto detects the right table for us
- Click Ok
- Transform Data
  
## In Power Query editor
- Got the page-1 first 50 records. But, we need to get the entire 106 records. So we need some M Query scripting
- Home tab
- Advanced editor
- M Query Command Line - change Page = 1 to Page = "&ps&" (this is a variable for the upcoming function).<br>
  Above "Let" define a function -: **(ps as text) =>**
- Go to "PROPERTIES", Name the function as - ESPN
- In the left function name ESPN area, right click, select - New Query -> Blank Query
- Go to formula bar (*fx*) create a list and write, = {1..3}, press enter
- Convert the list into a table - go to top left -> Click "To Table", click Ok
- Change the data type to a text (Left click ABC 123 on column1, select Text)
- In the Ribbon, go to - Add Column -> Invoke custom function -> New column name = Custom, Function query = ESPN, ps -> Column1
- Press Ok
- Expand ESPN, Load more, Default column name prefix(optional) - remove ESPN, Click Ok
- On the Ribbon click "View", See "Column profile", Count rows = 106, matches with the Original table in Web.
- Remove Column1
- Rename Column1.1 to Column1
  
## Setting Headers as per the web in Power Query
- Go to ESPN website table, copy the column names
- open an excel sheet and paste the names
- Copy the column names then in the next row type Cntrl+Alt+V to paste values
- Remove the first record, Cntrl - (minus)
- Copy the column names, go to power query, Home tab -> Enter data -> Paste column names, undo headers -> OK
  We can see that all the column names are in the first record, 1st row after column headers.
- Name the table as "Headers"
- Select Query1, from the Ribbon choose "Append Queries as New", first table Headers, second table Query1, click Ok
- Home tab, Use first row as Headers
- Clean and format every column to data type text, decimal or whole number.
- Rename the Appended table to Cricket Data from Append1.
- Hide other tables (Headers & Query1) for the report view.
- Cloase & Load


## Batting Headers Meaning
Player	-The name of the batsman whose performance state are being recorded.<br>

Span	- The duaration of the player's career (start year - end year).<br>

Mat	- The total number of matches the batsman has participated in.<br>

Inns	- The total number of innings the batsman has participated in.<br>

NO	- The total number of not-outs the batsman has been involved in.<br>

Runs	- The total number of runs scored by the batsman in all matches.<br>

HS	- "Highest Score: The highest number of runs runs the batsman has scored in all innings."<br>

Ave	- Batting Average: The average number of runs the batsman has scored per dismissal (Runs/Outs).<br>

BF	- Balls Faced: The ttotal number of balls faced by the batsman.<br>

SR -	Strike Rate: The number of runs scored per 100 balls faced (Runs/Ball * 100).<br>

100	- The number of centuries (100+ runs) score by the batsman.<br>

50	- The number of half-centuries (50+ runs) score by the batsman.<br>

0	- The number of times the batsman has been dismissed for a score zero.<br>

4s	- The number of boundaries (4s) scored by the batsman.<br>

6s	- The number of sixes (6s) scored by the batsman.<br>

## Bowling Headers Meaning
Overs - The total number of overs bowled by the player in all matches.

Mdns - THe total number of maiden overs bowled vy the player.

Runs - The total number of runs conceded by the bowler in all matches.

Wkts - The total number of wickets taken by the bowler.

BBI - Best Bowling Innings: The best bowling performance in a single innings (wickets/overs).

Econ - Economy Rate: The average number of runs conceded per over bowled (Runs/Overs).

SR - Strike Rate: The average number of balls bowled per wickettaken (Balls/Wkts).

4 - The number of times the bowler has taken 4 or more wickets in an innings.

5 - The number of times the bowler has taken 5 or more wickets in am innings.

## Fielding Headers Meaning
Dis - The total number of dismissals the player has been involved in (catches, stumpings).

Ct - The number of catches the player has taken in their career.

St - The number of stumpings made by the player.

Ct Wk - The number of catches the player has taken as a wicketkeeper.

Ct Fi - The number of catches taken by the player as a fielder (not as a wicketkeeper).

MD - The number of match days or the number of matches the player has played.

D/I - Dismissals per innings ratio, showing the number of dismissals per innings.

# Objective:
Create a three page Power BI report, each page should contain the details of Batting, Bowling and Fielding respectively.<br>
The user should be given the flexibility to select the name any given player and be able to see all the details of that particular player on each page. 
