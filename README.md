## MySQL IMDB PROJECT
**Project Overview:** 

The MYSQL-IMDB project is focused on creating a comprehensive database of movies using MySQL, designed to store and manage extensive data sourced from the IMDB database. The primary objective of this project is to develop an efficient and scalable database structure that supports various queries and analyses related to movies, genres, actors, directors, and other related entities. The project involves importing, preprocessing, and normalizing a dataset of movies, and creating a series of tables, views, stored procedures, and functions to facilitate complex queries and data analysis.

**Technologies Used:**

**Database Management System:** MySQL

**Data Import Tool:** phpMyAdmin

**Programming Language:** SQL

**Dataset Source:** Kaggle - IMDB Score Prediction for Movies (https://www.kaggle.com/code/saurav9786/imdb-score-prediction-for-movies)

**Preprocessing Steps:**

**Data Preprocessing:**

Before importing the data into MySQL, several preprocessing steps were carried out in Excel to ensure data quality and uniqueness.

**1. Data Deduplication:**

**Objective:** Remove duplicate records to ensure each movie is represented uniquely in the database.

**Method:** Used Excel's built-in features to identify and remove duplicate rows based on movie attributes such as title, year, and other relevant fields.

**2. Add Unique Identifier:**

**Objective:** Assign a unique identifier to each movie record to facilitate database management and relationship mapping.

**Method:** Added a new column called "movie_id" in Excel and populated it with unique values for each movie record.

**3. Genre Data Transformation:**

**Objective:** Normalize genre data to create a structured format suitable for relational database management. 

**Steps:**

**Copying Columns:** Copied the "movie_id" and "genre" columns from the unnormalized dataset ("movies-unf") to a separate tab in Excel.

**Text to Columns:** Used the "Text to Columns" feature in Excel, specifying a delimiter (e.g., pipe '|'), to split genres into unique columns.

**Saving as CSV:** Saved the transformed data as a CSV file with the "CSV UTF-8 (comma delimited) (.csv)" extension.

**Import Genre Data:**

**Objective:** Import the normalized genre data into MySQL.

**Method:** Used phpMyAdmin to import the CSV file ("movie_genre-unf") into the MySQL database.

**4. Repeat for Actors and Plot Keywords:**

**Objective:** Normalize and import data for actors and plot keywords. 

**Steps:**

**Data Transformation:** Followed the same steps as genre data transformation (copying columns, using text to columns, and saving as CSV).

**Data Import:** Imported the transformed data into MySQL using phpMyAdmin.

**5. Separate Columns:**

**Objective:** Normalize data related to countries, IMDB scores, languages, and content ratings.

**Steps:**

**Creating Individual Tabs:** Separated the columns for "country," "imdb_score," "language," and "content_rating" into individual tabs in Excel. 

**Combining with Movie ID:** In each tab, combined "movie_id" with the respective data (e.g., "movie_id" and "country" in one tab, "movie_id" and "language" in another tab).

**Saving as CSV:** Saved all tabs as CSV files with the "CSV UTF-8 (comma delimited) (.csv)" extension.

By following these preprocessing steps, the data was organized and cleaned, ready for import into MySQL. This ensured that the database was well-structured and prepared for further analysis and query operations.


