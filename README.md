# Data Modeling with Postgres

## Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. However, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.


The objective of this project is to create a star schema optimized for queries on song play analysis and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.


## Data
* Songs metadata: collection of JSON files that describes the songs such as title, artist name, duration, year, etc.
* Logs data: collection of JSON files where each file covers the users activities over a given day.


## Methodology
We'll build the database by optimizing the tables around efficient reads for complex queries. To do that, Star schema will be used utilizing dimensional modeling as follows:

* Fact table: songplays
* Dimensions tables: songs, artist, users, time


![sparkify_entity_relationship_postgresql](https://user-images.githubusercontent.com/6285945/75607578-9975c480-5b1e-11ea-9439-97d90c05d6ce.PNG)


The three most important advantages of using Star schema are:

* Denormalized tables
* Simplified queries
* Fast aggregation


## How to execute scripts
The source code is available in three separate Python scripts. Below is a brief description of the main files:

1. sql_queries.py has all the queries needed to both create/drop tables for the database as well as a SQL query to get song_id and artist_id from other tables since they are not provided in logs dataset
2. create_tables.py creates the database, establish the connection and creates/drops all the tables required using sql_queries module
3. etl.py build the pipeline that extracts the data from JSON files, does some transformation (such as adding different time attributes from timestamp) and then insert all the data into the corresponding tables


First run create_tables.py then etl.py to create the database, create tables, and then insert the data using the ETL pipeline.
