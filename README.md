## ProjectTableau

This repo contains all related data and informations for the Project Tableau of the Ironhack Data Analytics Bootcamp March 2020.

## Description

For performing a detailed investigation on the german election in 2017 with the Software _Tableau_ I've downloaded two datasets in .csv-format from kaggle.com. One file consists of the overall results (2017_german_election_overall.csv -> will be further referred as "Overall") and one contains informations of the votes for each party (2017_german_election_party.csv > will be further referred as "Party"). 

_Overall_ consists of

  Dimensions:
    - area_names
    - state

  Measures:
    - area_id
    - F1
    - invalid_first_votes
    - invalid_second_votes
    - registered.votes
    - total_votes
    - valid_first_votes
    - valid_second_votes
    
 _Party_ consists of

  Dimensions:
    - area_name
    - party
    - state

  Measures:
    - area_id
    - F1
    - votes_first_votes
    - votes_second_votes

Following steps in processing the data for the needed visualizations has been done:
  1. Import both files and join on the keyword _area_id_ 
      --> one set of joined _area_id_ consists of 299 rows with the result of one party. Since there are 43 parties, the full table has      
          12857 rows.
  2. Because needed values within one column are now 43 times higher when using the in-built SUM, calculated fields are made for
          - Total registered voters ('SUM([Registered voters])/COUNTD([Party])')
          - Valid first votes ('sum([Valid first votes])/COUNTD([Party])')
          - Valid second votes ('sum([Valid second votes])/COUNTD([Party])')
          - Percentage of invalid first votes ('[Invalid first votes]/[Total votes]')
          - Percentage of invalid second votes ('[Invalid second votes]/[Total votes]')
          - Percentage of valid first votes ('[Valid first votes]/[Total votes]')
          - Percentage of valid second votes ('[Valid second votes]/[Total votes]')
          - Voting results in % ('SUM([votes_second_vote])/SUM([Valid second votes])')
