# data-sourcing-challenge

The code file to run will be <retrieve_movie_data_edited.ipynb> and the output .csv file
for the results will be <nyt_tmdb_output.csv>. The <retrieve_movie_data.ipynb> file was 
a starter code file and was kept to use as reference and backup if the editing file was
lost or corrupted.

## Overview

We are asked to prepare data to help recommend people on finding movie reviews and related
movies. The task to is extract data from The New York Times and The Movie Database and then
merge the two together.

## Initial Preparation For Task

Our first step is to aquire the API keys for both the The New York Times and The Movie Database.
This allows us access to the data.

## Part 1: Access the New York Times API

When accessing the data from the New York Times, we set up a query url based on the following search
criteria of looking for "Movies" with "love" in the headline and the type of material "Reviews"
We sort the filter by "newest" between the dates of "20130101" and "20230531"

The NYT search will consist of 20 pages with a 12 second interval between queries. The data is then
stored in a JSON object dataframe. The dataframe is cleaned some so that keywords can be extracted.
A "titles" list will be created from the dataframe to then be passed to Part 2 of accessing the Movie
Database.

## Part 2: Access The Movie Database API

The "titles" list from Part 1 is used in the query url for the Movie Database to find the "movie ID".
After getting the "movie ID", the full movie details is extracted in JSON format. Then the "genres",
"spoken_languages", and "production_countries" are extracted from the JSON data. Finally, a dictionary
is created with  title, original_title, budget, original_language, homepage, overview, popularity, runtime, 
revenue, release_date, vote_average, vote_count, as well as the genres, spoken_languages, and production_countries 
lists.

## Part 3: Merge and Clean the Data for Export

This part we merge the two DataFrames from the NYT and TMDB, clean the data, and export it to a .csv file.
After merging the two DataFrames on the "Title" column, the "genres", "spoken_languages", and "production_countries"
columns will be cleaned. We will remove both the left and right square brackets along with the apostrophe in the 
strings. In the merged DataFrame, duplicate rows will be deleted and the index will be reset. Finally an output .csv
file is created without the DataFrame index.

## Final Thoughts and Notes on My Work

I believe the data from both the New York Times and the Movie Database may be dynamic and the data or articles
may change without notice. Therefore when this task/code is executed, the data may vary slightly for example if
either websites decide to modify or delete data/articles.

I did use the Xpert Learning Assistant to help with some of the code when accessing the Movie Database API.
I needed help and clarification of what was needed to build the dictionary for dataframe of the extracted
Movie Database API.