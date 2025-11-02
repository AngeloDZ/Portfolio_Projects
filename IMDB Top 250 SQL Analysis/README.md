# IMDB Top 250 SQL Analysis

## 1 Overview
This project explores the 250 top rated IMDB movies of all time using some basic SQL queries.

This is my first project, mainly for the purpose of a starter portfolio project and practicing some basic SQL queries on PostgreSQL, as well as learning how to use Github to display future projects.

## 2 Exploring the data

### 1) Viewing all the data

````sql
SELECT * FROM imdb_top_250_movies
ORDER BY year DESC
````

Very simple. Added ORDER BY clause for convenience.

### 2) Order all films by rating descending

````sql
SELECT title, rank, rating FROM imdb_top_250_movies
ORDER BY rating DESC
````
Again, very simple use of the ORDER BY clause.

### 3) Find movie(s) with the maximum rating

````sql
SELECT title, rank, rating FROM imdb_top_250_movies
WHERE rating = (SELECT MAX(rating) FROM imdb_top_250_movies)
````
I could have just used a WHERE clause to select the row with the number 1 rank, however I wished to use a basic subquery for the purposes of practice. Additionally, if the data contained more than one movie with the highest rating, those additional movies would be displayed too.

### 4) Find the top 10 movies of all time.

````sql
SELECT title, rank FROM imdb_top_250_movies
WHERE rank <= 10
ORDER BY rank;
````
Two ways of doing this. First is the WHERE clause with regards to the rank.

````sql
SELECT title, rating FROM imdb_top_250_movies
ORDER BY rating DESC
LIMIT 10;
````
Second is by using LIMIT.

### 5) Find all the movies with a rating of 9 or higher.

````sql
SELECT title, year, rating FROM imdb_top_250_movies
WHERE rating >= 9
ORDER BY rating DESC
````
Again, simple use of the WHERE clause.
