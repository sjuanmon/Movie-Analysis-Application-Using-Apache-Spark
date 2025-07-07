# 🎬 Movie Analysis Application Using Apache Spark

## 📊 Overview
This project focuses on analyzing structured data related to movies using Apache Spark. The main objective is to explore and derive insights from a dataset containing movie details and reviews, including genres, ratings, and release dates.

## 🎯 Objectives

Display movie details without truncating long text fields.
Rename columns in the reviews DataFrame for clarity.
Join movie details with reviews based on the movie ID.
Explode the genres column to analyze the average ratings by genre.
Analyze the release years to identify the years with the highest number of released movies.

## ⚙️ Technologies Used

Apache Spark (Python API)
Jupyter Notebooks

## 🚀 Getting Started

Clone the repository to your local machine.
Ensure you have Apache Spark installed along with the necessary Python libraries.
Open the Jupyter Notebook and run the provided code cells sequentially.

## 🌟 Features

Display Movie Details: The application demonstrates how to show movie details without truncating long text fields using the show() method.
DataFrame Manipulation: Includes renaming columns and joining DataFrames to create a comprehensive dataset.
Genre Analysis: Explodes the genre column to compute average ratings for each genre, providing insights into audience preferences.
Release Year Analysis: Identifies the top 10 years with the highest number of movie releases, allowing for trend analysis over time.

## 💻 Code Snippets

### Show Movie Details Without Truncation
Codemovie_details.show(truncate=False)

### Rename Column in Reviews DataFrame
Codereviews_renamed = reviews_details.withColumnRenamed("rating", "review_rating")

### Join Movie Details and Reviews
Codemovies_with_ratings = movie_details.join(reviews_renamed, on="movie_id", how="left")

### Explode Genre and Calculate Average Ratings
Codemovies_with_ratings_exploded = movies_with_ratings.withColumn("genre", F.explode("genre"))rating_by_genre = movies_with_ratings_exploded.groupBy('genre').agg(F.avg('review_rating').alias('avg_rating'))rating_by_genre.show()

### Analyze Release Years
Codemovies_with_year = movie_details.withColumn("release_year", F.year("release_date"))movies_by_year = movies_with_year.groupBy("release_year").count()top_10_years = movies_by_year.orderBy(F.desc("count")).limit(10)top_10_years.show()

## 📈 Results

The analysis provided insights into average ratings by genre and the years with the highest number of movie releases.
The results can assist in understanding trends in the film industry and audience preferences.
