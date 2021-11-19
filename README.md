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

As the above image shows, most of the raw data movie ratings in this dataset were 3.0 or 4.0 (click on image to enlarge).

# Initial Models Used

* KNNBasic (K-Nearest Neighbors)
* KNNWithMeans
* KNNWithZScore
* SVD (Single Value Decomposition)
* SVDpp
* NMF (Non-Negative Matrix Factorization)

# Initial Model Results

* KNNBasic - RMSE: 0.9470, MAE: 0.7256
* KNNWithMeans - RMSE: 0.8961, MAE: 0.6847
* KNNWithZScore - RMSE: 0.8970, MAE: 0.6802
* SVD - RMSE: 0.8725, MAE: 0.6706**
* SVDpp - RMSE: 0.8613, MAE: 0.6598**
* NMF - RMSE: 0.9215 , MAE: 0.7065

**Models that performed the best (lowest RMSE and MAE)

# Final Model

I conducted hyperparameter tuning using GridSearch for the two models that performed the best. Based on the results from GridSearch, I chose SVD as my final model:

![image](https://user-images.githubusercontent.com/77416319/142633674-c7d3e3c2-061d-4386-a944-7a08c7ffedea.png)

The image above is a snapshot of the actual ratings and the predicted ratings. The predicted ratings were fairly close to the actual ratings (click on image to enlarge). 

![image](https://user-images.githubusercontent.com/77416319/142577006-fc704384-b5b1-4e38-bd5e-023b86802f12.png)

From the scatter plot above, the model underpredicted movies that were rated 4 or 5, while it overpredicted movies that were rated 1 or 2. This indicates that the rating system recommends movies that users gave a low rating overall (1 and 2) and doesn't recommend movies that were highly rated (4 and 5) (click on image to enlarge).

![image](https://user-images.githubusercontent.com/77416319/142577037-d8914b4f-cbe2-4398-8d28-b8c361d61411.png)

The image above is the residual error of the predictive model. The actual ratings of the data were overpredicted within 1 or underpredicted within -1 (click on image to enlarge).

# Popularity Bias

* Popular items that are overly exposed in recommendations at the expense of less popular items that users may find interesting.
* Hurts both users and items; users worse off-system only learns biased view of their true preferences.
* Popular does not equal better.
* Less popular items lose deserved feedback(clicks/views) + economic gains.

**Source: http://people.tamu.edu/~zhaoxing623/publications/Ziwei_KDD_2021.pdf

# Factors Impacting Popularity Bias

* Audience Size Imbalance, Model Bias, Position Bias, Closed Feedback Loop.
* Audience Size Imbalance: inherent imbalance-few items have large audience size, majority have small audience size; results in imbalance engagement data (clicks), even if every item is equally recommended.
* Model Bias: rank item with more clicks/views in training data higher than item with fewer clicks/views, even if user equally likes both items.
* Position Bias: probability to examine items at top ranking positions is higher than at lower positions; matched popular item being recommended and ranked at a top position is more likely to receive click/view than a matched but unpopular item also being recommended but ranked in lower position.
* Closed Feedback Loop: popularity bias generated in past accumulates, producing more bias in future models.
**Source: http://people.tamu.edu/~zhaoxing623/publications/Ziwei_KDD_2021.pdf

# Predicted Ratings of 1 User

![image](https://user-images.githubusercontent.com/77416319/142638992-0cc15baf-7b71-49a9-815f-a63440eddbe1.png)

The image above is a bar plot showing the predicted ratings of 1 user based on movie genre. As the image illustrates, Documentary and Film-Noir were the highest-rated genres for this particular user. These two genres are not traditionally among the most popular genres among users, and could indicate that popularity bias is mitigated in this recommendation system model (click on image to enlarge). 

# Final Conclusions

* SVD - best performing recommendation system model.
* Predicted ratings error between 1 and -1.
* Predicted ratings for one user based on movie genre-may help mitigate popularity bias.

# Next Steps

* Look beyond movies - include television shows.
* Compare movie ratings with television ratings.
* Include other features that may determine what impacts user ratings, i.e. actors, actresses, directors, etc.
* Data on features of users (i.e. Age, Gender) and examine any trends related to how the rated movies/television shows. 
* Consider user behavior since beginning of COVID-19 pandemic.
* Explore popularity bias in future models.
