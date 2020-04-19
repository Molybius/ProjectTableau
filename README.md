# ProjectTableau

This repo contains all related data and informations for the Project Tableau of the Ironhack Data Analytics Bootcamp March 2020.

_Important: I've failed several times to publish the Tableau story via the Software (using full version 2020.1). After some research online the problem seems to be on the software suppliers side since I encountered exactly the same problems as described in following thread: https://community.tableau.com/thread/286376 . I was able to save the story as a powerpoint presentation which I added to the data folder as well as the native Tableau file._

# Description
## Data handling

For performing a detailed investigation on the german election in 2017 with the Software _Tableau_ I've downloaded two datasets in .csv-format from kaggle.com. One file consists of the overall results (2017_german_election_overall.csv -> will be further referred as "Overall") and one contains informations of the votes for each party (2017_german_election_party.csv > will be further referred as "Party"). 

_Overall_ consists of

  Dimensions: <br />
    - area_names <br />
    - state <br />

  Measures:
    - area_id <br />
    - F1 <br />
    - invalid_first_votes <br />
    - invalid_second_votes <br />
    - registered.votes <br />
    - total_votes <br />
    - valid_first_votes <br />
    - valid_second_votes <br />
    
 _Party_ consists of <br />

  Dimensions: <br />
    - area_name <br />
    - party <br />
    - state <br />

  Measures: <br />
    - area_id <br />
    - F1 <br />
    - votes_first_votes <br />
    - votes_second_votes <br />

Following steps in processing the data for the needed visualizations has been done: <br />
  1. Import both files and join on the keyword _area_id_  <br />
      --> one set of joined _area_id_ consists of 299 rows with the result of one party. Since there are 43 parties, the full table has 12857 rows. <br />
  2. Because needed values within one column are now 43 times higher when using the in-built SUM, calculated fields are made for <br />
          - Total registered voters <br />            ('SUM([Registered voters])/COUNTD([Party])') <br />
          - Valid first votes     <br />              ('sum([Valid first votes])/COUNTD([Party])') <br />
          - Valid second votes    <br />              ('sum([Valid second votes])/COUNTD([Party])') <br />
          - Percentage of invalid first votes <br />  ('[Invalid first votes]/[Total votes]') <br />
          - Percentage of invalid second votes <br /> ('[Invalid second votes]/[Total votes]') <br />
          - Percentage of valid first votes  <br />   ('[Valid first votes]/[Total votes]') <br />
          - Percentage of valid second votes <br />   ('[Valid second votes]/[Total votes]') <br />
          - Voting results in %         <br />        ('SUM([votes_second_vote])/SUM([Valid second votes])') <br />
  
      In-built data handling (f.e. avearge, count distinct, etc) as well as quick table calculations (f.e. percent of total, etc) has been used for further data processing to generate needed visualizations.
      
## Data visualization
The principal aim for the final story was to display the overall result, showing parties passing/unpassing the 5% hurdle, showing the relative amount of valid/invalid votes of both first and second vote for each state, highlighting how areas voted for the main parties as well as a closer look on the AfD and DIE LINKE.

## Obstacles encountered
I intended to investigate the data with a granularity down to the constituencies. The software stated the need of textfile, which I imported without an error message, but the data weren't available. After trying several hours to fix that problem (which failed) I decided to stick to the state level in order to avoid more time losses.

## Results of investigation
Please refer following worksheet descriptions to the Tableau Story accesible via the link in next chapter. <br />
Worksheet _Final election results_ <br />
    Shows the overall election results with a 5%-threshold line, which is the hurdle for entering the german Bundestag.
   
Worksheet _Parties of the new Bundestag_ <br />
    Shows a bar chart of all parties who passed the 5% hurdle and are part of the Bundestag (CDU, SPD, FDP, Bündnis90/Die Grünen, DIE LINKE, AfD).
    
Worksheet _Failed parties_ <br />
    Shows a bar chart of all parties who missed the 5% hurdle and are not part of the Bundestag.
    
Worksheet _Invalid first votes per state_ <br />
    Shows a heatmap of all states highlighting invalid first votes. Bayern has the least with 0.95%, Sachsen-Anhalt the most with 1.81%.
 
Worksheet _Invalid second votes per state_ <br />
    Shows a heatmap of all states highlighting invalid second votes. Bayern has the least with 0.66%, Saarland the most with 1.70%.
 
Worksheet _AfD vs. DIE LINKE_ <br />
    Shows two heatmaps with voting results for the parties AfD and DIE LINKE. It can be clearly seen that both parties are mainly elected in the former eastern part of Germany. An possible explanation for DIE LINKE is it's historical connection to former eastern Germany which overlaps with their politic goals. In western Germany,  the state of Saarland elected DIE LINKE with a relativly high proportion, most likely because the former chairman was the prime minister there between 1985-1998. The strong result for the Afd are probably based on socio-economic aspects, which needs a deeper analysis.
    
Worksheet _Comparision of other parties_ <br />
    Shows 5 heatmaps of all main parties (except of a.m.) and in which state each has mainly been elected. All shown parties are more or less evenly elected over Germany whereas SPD is relativly strong in north-west Germany.
    

Worksheet _Select party result per state_ <br />
    Shows a map of all states with the possibility to select one of the 43 parties and show it's result per state.

## Links
Tableau (unable to publish, please refer to initial statement)

