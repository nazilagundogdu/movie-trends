Being movie fans, my husband and I noticed a subtle decline in the script quality of more contemporary movies. The Data Scientist in me was triggered to see whether our perceptions can be substantiated. I got to work and would like to share some of my findings with you.
 

🎦 Linear Regression on Oscar-nominated and winner movie ratings
After choosing IMDB as my main source because of its popularity and completeness, step one was to actually find the list of Oscar-nominees. Using the BeautifulSoup library in Python I pulled the names and the years for Oscar-nominees for “best picture” in the past 50 years (note this analysis does not look at best actor/actress or other categories).
 

This was followed by extracting the  links for each movie as I wanted to pull more detailed data. The data I was interested in included the overall IMDB rating, the name of the Director and the Cast, as well as whether the movie finally won the award or not.
 
 
This left me with 311 nominees and, well, 50 winners. The following diagram shows the trend of ratings for winners in the past 50 years.


![Average Ratings By Movie](/Movie-Trends/average_ratings_by_movie.png) 



Although very subtle, the ratings show an overall decline. The average rating for the winners is 7.69, with the highest score belonging to The Godfather (1973): 9.2, and the lowest one being shared among the three movies of Chariots of Fire (1982), Out of Africa (1986) and Shakespeare in Love (1999) with the rating of 7.1.

 
Expanding the visualization to all 311 nominated movies, and running a Linear Regression analysis, the decline in ratings become slightly more visible. The Mean Absolute Error (MAE) for training and test data is as the following:
 
Training MAE: 0.37
Testing MAE: 0.41
 
The model predicts a rating of 7.65 for year 2030.
 
![Linear Regression on Oscar-Nominated Movies](/Movie-Trends/linear-regression-rating-by-year.png)


🎦🎦 K-means clustering of Directors based on Oscar-nominated and winner movie ratings
 
I was almost sure Martin Scorsese would be at the top of the list, and boy, was I wrong!
 
The following graph shows the average rating for directors of best motion pictures in the past 50 years in descending order. And to my surprise, Martin Scorsese is 7th on the list with average rating of 8.5, with Francis Ford Coppola taking the highest-ranking Director with average rating of 9.1. I am sure it will be a different story if we included other categories in the mix (maybe something for future work).


![Average Rating by Directors of Oscar Winners](/Movie-Trends/average_ratings_by_director.png)


Looking at all directors with Oscar-nominated movies, the story changes and we get “Frank Darabont” at the top, with an average rating of 8.95 (of course, who does not like “The Shawshank Redemption” or “The Green Mile”!). 

![Average Rating by Directors of Oscar Nominees](/Movie-Trends/average_ratings_by_nominee_movie.png)


In order to see how ratings plus number of movies correlate with each other, I did a K-means clustering of the Directors based on these two features.
 
Using the Elbow Method to determine the optimal number of clusters, I landed on #4 clusters.
 
![Elbow Method](/Movie-Trends/elbow-method.png)

Lack of clarity on the cut-off point in the elbow diagram, made me use the Silhouette Method as a means of confirmation. The Silhouette Method also converges on 4, with the silhouette coefficient being the maximum with 4 clusters.

![Silhouette Method](/Movie-Trends/silhouette-method.png)


The following diagram shows the clustering of directors based on the ratings they got and the number of Oscar-nominated movies they have directed.


![K-means Clustering of Directors](/Movie-Trends/4-k-means-clustering.png)

 
The highest-ranking directors are clustered as “Steven Spielberg” + “Martin Scorsese” at the top. This is followed by Clint Eastwood, Ang Lee, and so on (the list is too long to fit). Seeing Martin Scorsese in the top right cluster made me happy!



