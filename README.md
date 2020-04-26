# ETL pipeline with Python and PostgreSQL/ Apache Cassandra
Two ETL pipelines using Python and PostgreSQL/Apache Cassandra: 
1. Postgres database and ETL pipeline that model song and log datasets (~ 8,000 records). The database is designed with star schema to optimize queries on music analysis.
2. Apache Cassandra database and ETL pipeline with more than 8,000 records for users' behaviors analysis
- The project includes 5 files and 2 folders:
1. __test.ipynb__ - displays the first few rows of each table to let you check your database.
2. __create_tables.py__ - drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
3. __etl.ipynb__ - reads and processes a single file from song_data and log_data and loads the data into tables. This notebook contains detailed instructions on the ETL process for each of the tables.
4. __etl.py__ - reads and processes files from song_data and log_data and loads them into your tables.
5. __sql_queries.py__ - contains all sql queries, and is imported into the last three files above.
6. __data__ - folder contains datasets
7. __Apache Cassandra__ - folder contains data modeling with Cassandra

## Schema Design

![Star Schema](./star_schema.png)

#### 1. Fact Table
- __songplays__ - records in log data associated with song plays i.e. records with page NextSong
    - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
#### 2. Dimension Tables
- __users__ - users in the app
    - user_id, first_name, last_name, gender, level
- __songs__ - songs in music database
    - song_id, title, artist_id, year, duration
- __artists__ - artists in music database
    - artist_id, name, location, latitude, longitude
- __time__ - timestamps of records in songplays broken down into specific units
    - start_time, hour, day, week, month, year, weekday
## ETL process
1. Populate the songs and artists tables with data derived from the JSON song files, data/song_data. 
2. Populate time and users tables with data derived from the JSON log files, data/log_data
3. Populate the songplays fact table by using a SELECT query that collects song_id and artist_id from the songs and artists tables and log file data

## Running Instruction
#### 1. Install [PostgreSQL](https://www.postgresql.org/) and [Python](https://www.python.org/)
#### 2. Create Database and Relations 
```
$ python create_tables.py
```
#### 3. Extract, Transform, and Load Data into Relations
```
$ python etl.py
```
