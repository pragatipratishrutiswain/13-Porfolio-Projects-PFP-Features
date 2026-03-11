## In this project we will do -
1️⃣ Web Scrapping in Power BI<br>
2️⃣ Use publicly available ESPN cricket data online<br>
3️⃣ We are interested only in ODIs

## Getting the data:
- Google search bar
- Search "espn cricinfo statsguru"
- Select "ODI"
- Select "Batting"
- Team: India
- Opposition: Australia
- Home or away: home
- Submit query

## Power BI desktop page set up. Go to
- File
- Options & settings
- Options
- Data load
- Type Detection
- Select option 3: "Never detect column types and headers for unstructured sources."

## For Web as the Data Source, select
- Get Data
- Web
- URL
- Stay "Anonymous"
- Click Ok

# Method 1 - Incase of Multiple tables 
- Select table - "Overal Figures"
- Choose "Transform"

## In Power Query editor
-- Home
-- Use first row as headers
-- Remove last column (Unnecessary column)
-- Close & Apply
 
# Method 2 - Incase of Multiple table
- Add table using examples
- Copy the first row from the original table
- Copy the second row from the original table
- Now Power BI auto detects the right table for us
- Click Ok
- Transform Data
  
## In Power Query editor
-- 

