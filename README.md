![image](https://github.com/user-attachments/assets/bc59486f-ec71-494a-845e-8897a6f6649e)

# ETL load PostgresSQL Specific Excel Value Using Talend Open Studio For Big Data
Using Iterate Flow, one of component in Talend, filter data from specific columns in excel list and load it to PostgreSQL Database

The purpose of this project is to extract dataset from csv online using Talend Open Studio, transform with several basic technique using tmap component on Talend. The next one is storing to big query data lake. From data lake table, filter exclude null or No Data, filter just all teams from Pacific Division. Finnaly, Storing into Big Query Data Warehouse for Pacific Division Teams.

Download Dataset file : https://media.geeksforgeeks.org/wp-content/uploads/nba.csv

## Goals of the Project:
1.  Ingest Data csv using Talend Component
2.  Storing data PostgreSQL
3.  Filter using tFlowToIterate on Talend Component.
4.  Storing fileterd data to PostgreSQL
## prerequisite
1.  Using Talend Open Studio for Big Data
2.  Using Java 11
3.  PostgreSQL on local computer
## Lesson Result
1.  After download csv dataset to my local computer, create tFileInputDelimited and open nba dataset file. Field separator "," and Header 1. Row main to tDBOutput.
2.  Adding tDBOutput. Choose PostgreSQL as Database  and Config the credentials needed such as host,database,user,password,table_name. Choose create table if does not exists.
3.  Adding tFileInputExcel. Choose file does have list value for filtering data.
4.  Adding tFlowToIterate. add key "name" and value name.
5.  Adding tDBInput. Choose PostgreSQL as Database  and Config the credentials needed such as host,database,user,password,table_name.
6.  Create Query on tDBInput and add stringMap on where clause by name :
   
     "select nba_player.name,nba_player.team,
        nba_player.number,nba_player.position,
        nba_player.age,nba_player.height,
        nba_player.weight,nba_player.college,nba_player.salary
    from nba_player
    where nba_player.name = '"+((String)globalMap.get("name"))+"'
    order by nba_player.name asc"
    
8.  Adding tDBOutput. Choose PostgreSQL as Database  and Config the credentials needed such as host,database,user,password,table_name. Choose create table if does not exists.
