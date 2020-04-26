# ETL pipeline with Python and PostgreSQL
Postgres database models song and log datasets to produce star schema. The model is optimized for retrieving data to perform music analysis.

## Schema Design
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
## ETL pipeline
- Populate the songs and artists tables with data derived from the JSON song files, data/song_data. 
- Populate time and users tables with data derived from the JSON log files, data/log_data
- Populate the songplays fact table by using a SELECT query that collects song_id and artist_id from the songs and artists tables and log file data

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
