# DATA MODELING WITH POSTGRES

## Table of contents
* [General info](#general-info)
* [Files](#files)
* [Technologies](#technologies)
* [Setup](#setup)


## General info
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to.
The aim of this project is to create a Postgres database with tables designed to optimize queries on song play analysis. For this a database schema and ETL pipeline for this analysis are created.
The following data sets are provided:

### Song Dataset
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

### Log Dataset
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.
The log files in the dataset you'll be working with are partitioned by year and month.

[star](starschema.jpg)

Using the song and log datasets, a star schema optimized for queries on song play analysis was created. This includes the following tables.
Fact Table
	1. songplays - records in log data associated with song plays i.e. records with page NextSong
		○ songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
Dimension Tables
	2. users - users in the app
		○ user_id, first_name, last_name, gender, level
	3. songs - songs in music database
		○ song_id, title, artist_id, year, duration
	4. artists - artists in music database
		○ artist_id, name, location, latitude, longitude
	5. time - timestamps of records in songplays broken down into specific units
		○ start_time, hour, day, week, month, year, weekday


## Files
The project includes six files:
	1. test.ipynb displays the first few rows of each table to let you check your database.
	2. create_tables.py drops and creates the tables. You run this file to reset your tables before each time you run your ETL scripts.
	3. etl.ipynb reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
	4. etl.py reads and processes files from song_data and log_data and loads them into your tables.
	5. sql_queries.py contains all the sql queries, and is imported into the last three files above.


## Technologies
This project was developped on the workspace provided by Udacity.

## Setup
To run this project, run the following code in the console:

```
$ python create_tables.py
$ python etl.py
```


