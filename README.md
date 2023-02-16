# SOEN 471 Project - BookForYou (Team 39)


## Project definition
One of the biggest challenges when wanting to read books is finding the right book to read. That is why we made BookForYou. BookForYou is a recommender system that suggests books for the user based on their inputted preferences for author, title, and book category. It uses book reviews from Amazon’s Book database to find the ideal book candidate.

## Model design

The dataset used is [Amazon Book Reviews](https://www.kaggle.com/datasets/mohamedbakhet/amazon-books-reviews?select=Books_rating.csv). 

The dataset consists of two entities, one with book details and the second containing book reviews. Each entity has 10 features, for a combined dataset size of 3.04 GB. As shown below, one book can have many reviews, but a review can only belong to a single book. Books are identified by their titles. From the book details, the title, author, year and category will be used. From the reviews entity, the content of the reviews, book rating, and the helpfulness rating of a given review will be used. 

<p align="center">
  <img src="https://i.imgur.com/9ELRD7G.png" alt="Book review dataset relationship schema"/>
</p>

## Research Question

Using Amazon Book Reviews dataset, recommend the ideal book that has similar attributes to the user based on their inputted book preferences.

## Class of Models

### Content based
A user will define an item profile by specifying their preferences for books. These preferences will be the basis of the user profile that will be created. Using this profile, books with similar attributes will be retrieved from the dataset and returned to the user to find the ideal suggestion. 

### Collaborative
A user will define their preference by specifying attributes of a book. Using explicit data gathering, users who have given high ratings to books with similar attributes will be considered as users who share common preferences. The other books that these users have given high ratings will then be recommended to the initial user to find the ideal suggestion.

## Algorithms

### K-means clustering
This algorithm consists of representing the data as a user-item ratings matrix in a vector space, where each item is mapped to a dimension in the space. K-means clustering will then group similar users or items together and the number of clusters k will be picked given the size of the dataset. Each of these clusters will be based on the features that belong to it ex: price and review. In order to make these recommendations, the model will be able to identify which clusters a user belongs to.

### CURE clustering
Similar to k-means clustering, the data representation will use a user-item ratings matrix. Then, the CURE algorithm will be utilized to group similar items together based on hierarchical clustering. Each cluster will then be represented by a set of representative points according to its distance to the centroid. The model will identify to which clusters the user belongs.
