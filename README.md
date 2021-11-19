# Recommedation System Project

# Overview

With streaming services more popular now than ever before, there are an extensive catalog of movies that users may find to be overwhelming. For this reason, a recommendation system is helpful to organize and steamline recommended movies based on ratings users provide. As a startup, it is essential to establish a recommendation system that helps current and future users to navigate the collection of movies in the streaming service and caters to their interests based on how they rate movies they have watched. This project will illustrate the mechanics of a recommendation system and why it is important for creating a streaming service. 

# Data Source and Details

* MovieLens dataset - contains links, tags, ratings and movies.
* Ratings - User ID, Movie ID, Rating, Timestamp
* Movies - Movie ID, Movie, Genre
* Over 100,000 rows of data


# Data Cleaning/EDA

* No missing values.
* Dropped column - timestamp.

# Distribution of Movie Ratings

![image](https://user-images.githubusercontent.com/77416319/142574165-cb5d62d2-f727-459c-91ef-75f2c73a192b.png)

As the above image shows, most of the raw data movie ratings in this dataset were 3.0 or 4.0.

# Initial Models Used

* KNNBasic (K-Nearest Neighbors)
* KNNWithMeans
* KNNWithZScore
* SVD (Single Value Decomposition)
* SVDpp
* NMF (Non-Negative Matrix Factorization)

# Final Model

