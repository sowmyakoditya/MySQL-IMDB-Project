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

**7. Separate Columns:**

 Separated the columns for "country," "imdb_score," "language," and "content_rating" 
into individual tabs.

• In each tab, combined "movie_id" with the respective data (e.g., "movie_id" and 
"country" in one tab, "movie_id" and "language" in another tab).

• Saved all tabs with "CSV UTF-8 (comma delimited) (.csv)" extension. 

**8. Imported Additional Data:**

Imported the unnormalized datasets "movie_language-unf," "movie_country-unf," 
"movie_content_rating-unf," and "movie_imdb_score-unf" into the MySQL database 
using phpMyAdmin.

By following these preprocessing steps, the data was organized and cleaned, ready for import into MySQL. This ensured that the database was well-structured and prepared for further analysis and query operations.

## Database Creation and Data Insertion:

Started creating tables movie, genre, movie_genre, plot_keyword, movie_plot_keyword, actor, movie_actor, director, language, country, imdb, content_rating and inserted the values to respective tables by performing joins.

**1. Creating Tables:**

Created tables movie, genre, movie_genre, plot_keyword, movie_plot_keyword, actor, movie_actor, director, language, country, imdb, and content_rating.

**2. Inserting Data:**

Inserted values into the respective tables by performing joins and ensuring data integrity.

INSERT INTO movie (movie_id, movie_title, color, duration, gross, imdb_url, language, country, content_rating, budget, title_year, imdb_score, aspect_ratio)
SELECT DISTINCT movie_id, movie_title, color, duration, gross, movie_imdb_link, language, country, content_rating, budget, title_year, imdb_score, aspect_ratio 
FROM movies_unf;

INSERT INTO director (director)
SELECT DISTINCT director_name FROM movie_director_unf WHERE director_name NOT IN (select director from director);

INSERT INTO movie_director(movie_id, director_id)
SELECT mdu.movie_id, d.director_id
FROM movie_director_unf mdu 
JOIN director d ON mdu.director_name = d.director;

INSERT INTO actor (actor_name)
SELECT DISTINCT actor_3_name FROM movie_actor_unf WHERE actor_3_name NOT IN (select actor_name from actor);

INSERT INTO movie_actor (movie_id, actor_id)
SELECT mau.movie_id, a.actor_id
FROM movie_actor_unf mau 
JOIN actor a ON mau.actor_3_name = a.actor_name;

INSERT INTO plot_keyword (plot_keyword)
SELECT DISTINCT plot_keywords5 FROM movie_plot_keywords_unf WHERE plot_keywords5 NOT IN (select plot_keyword from plot_keyword);

INSERT INTO movie_plot_keyword (movie_id, plot_keyword_id)
SELECT mpku.movie_id, pk.plot_keyword_id
FROM movie_plot_keywords_unf mpku 
JOIN plot_keyword pk ON mpku.plot_keywords5 = pk.plot_keyword;

INSERT INTO genre (genre)
SELECT DISTINCT genre8 FROM movie_genre_unf WHERE genre8 NOT IN (select genre from genre);

INSERT INTO movie_genre (movie_id, genre_id)
SELECT mgu.movie_id, g.genre_id
FROM movie_genre_unf mgu 
JOIN genre g ON mgu.genre8 = g.genre;

INSERT INTO language (language)
SELECT DISTINCT language FROM movie_language_unf WHERE language NOT IN (select language from language);

INSERT INTO country (country)
SELECT DISTINCT country FROM movie_country_unf WHERE country NOT IN (select country from country);

INSERT INTO imdb (imdb_score)
SELECT DISTINCT imdb_score FROM movie_imdb_unf WHERE imdb_score NOT IN (SELECT imdb_score FROM imdb);

INSERT INTO content_rating (content_rating)
SELECT DISTINCT content_rating FROM movie_content_rating_unf WHERE content_rating NOT IN (SELECT content_rating FROM content_rating);


**Constructed Database Objects:**

**Views**

MoviesWithGenreLangauage

MovieWithPlotKeywordAndContentrating

MovieWithGenre

MovieWithPlotkeyword

MoviesWithLanguage

MoviesWithCountry

MoviesCountByActor

MoviesByActor

**Stored Procedures:**

GetMoviesByLanguageAndCountry

GetMoviesReleasedAfterDate

GetMoviesReleasedAfterYearOrdered

GetMoviesByContentRating

**Functions:**

GrossAdjustedForInflation

AverageIMDBRatingForActor

TotalGrossByGenre

**Reverse Engineering:**

The initial ERD considered intersection tables for relationships like movie_director, but upon closer analysis, adjustments were made to reflect the correct relationships:

The relationship between movies and directors is Many-to-One (M:1).

The relationship between movies and IMDB scores is also Many-to-One (M:1).

**Results:**

Created a well-structured and scalable database that supports complex queries and analyses.

Improved data organization and retrieval efficiency.

Enabled detailed insights into movie data, genres, actors, directors, and other related entities.








