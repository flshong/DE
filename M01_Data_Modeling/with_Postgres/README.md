# Data Modeling with Postgres

In this project, you’ll model user activity data for a music streaming app called Sparkify. You’ll create a relational database and ETL pipeline designed to optimize queries for understanding what songs users are listening to. In PostgreSQL you will also define Fact and Dimension tables and insert data into your new tables.

### Datasets
1. Song Dataset - Complete details and metadata about the song
2. Log Dataset - User activity log

### Database Schema
The schema used for this exercise is the Star Schema: <br/>
One main fact table containing all the measures associated to each event (user song plays), <br/> 
and 4 dimentional tables, each with a primary key that is being referenced from the fact table.

#### Fact Table
**songplays** - records in log data associated with song plays i.e. records with page NextSong
- songplay_id (INT) PRIMARY KEY: ID of each user song play 
- start_time (DATE) NOT NULL: Timestamp of beggining of user activity
- user_id (INT) NOT NULL: ID of user
- level (TEXT): User level {free | paid}
- song_id (TEXT) NOT NULL: ID of Song played
- artist_id (TEXT) NOT NULL: ID of Artist of the song played
- session_id (INT): ID of the user Session 
- location (TEXT): User location 
- user_agent (TEXT): Agent used by user to access Sparkify platform

#### Dimension Tables
**users** - users in the app
- user_id (INT) PRIMARY KEY: ID of user
- first_name (TEXT) NOT NULL: Name of user
- last_name (TEXT) NOT NULL: Last Name of user
- gender (TEXT): Gender of user {M | F}
- level (TEXT): User level {free | paid}

**songs** - songs in music database
- song_id (TEXT) PRIMARY KEY: ID of Song
- title (TEXT) NOT NULL: Title of Song
- artist_id (TEXT) NOT NULL: ID of song Artist
- year (INT): Year of song release
- duration (FLOAT) NOT NULL: Song duration in milliseconds

**artists** - artists in music database
- artist_id (TEXT) PRIMARY KEY: ID of Artist
- name (TEXT) NOT NULL: Name of Artist
- location (TEXT): Name of Artist city
- lattitude (FLOAT): Lattitude location of artist
- longitude (FLOAT): Longitude location of artist

**time** - timestamps of records in songplays broken down into specific units
- start_time (DATE) PRIMARY KEY: Timestamp of row
- hour (INT): Hour associated to start_time
- day (INT): Day associated to start_time
- week (INT): Week of year associated to start_time
- month (INT): Month associated to start_time 
- year (INT): Year associated to start_time
- weekday (TEXT): Name of week day associated to start_time


### Steps to run:
1. Run create_tables.py : to drop database if exist and create a new datase with new tables are created.
2. Run test.ipynb in Jupyter Notebook to verify interactively that all tables are created correctly.
3. Run etl.py : to run the etl pipeline and extract data from the log files and insert them into the facts and dimension table