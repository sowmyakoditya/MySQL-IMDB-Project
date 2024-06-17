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

**3. Import Movies Data:**

Imported the unnormalized dataset "movies-unf" using phpMyAdmin.

**4. Genre Data Transformation:**

• Copied the "movie_id" and "genre" columns from "movies-unf" to a separate tab. 

• Utilized the "Text to Columns" feature, specifying delimiter settings (e.g., pipe), to 
create unique columns for each genre. 

• Saved this transformed data as a CSV file with "CSV UTF-8 (comma delimited) 
(.csv)" extension. 

**5. Import Genre Data:**

Imported the unnormalized dataset "movie_genre-unf" using phpMyAdmin. 

**6. Repeat for Actors and Plot Keywords:**

Followed the same steps (steps 4 to 5) for actors and plot keywords, creating separate 
tabs and applying text-to-columns for data transformation.

**5. Separate Columns:**

 Separated the columns for "country," "imdb_score," "language," and "content_rating" 
into individual tabs.

• In each tab, combined "movie_id" with the respective data (e.g., "movie_id" and 
"country" in one tab, "movie_id" and "language" in another tab).

• Saved all tabs with "CSV UTF-8 (comma delimited) (.csv)" extension. 

6. **Imported Additional Data:**

Imported the unnormalized datasets "movie_language-unf," "movie_country-unf," 
"movie_content_rating-unf," and "movie_imdb_score-unf" into the MySQL database 
using phpMyAdmin.

By following these preprocessing steps, the data was organized and cleaned, ready for import into MySQL. This ensured that the database was well-structured and prepared for further analysis and query operations.








