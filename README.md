# News Recommendation System

## Table of Contents
- [Introduction](#introduction)
- [Problem Statement](#problem-statement)
- [Data Description](#data-description)
- [Approach](#approach)
  - [Data Pre-processing](#data-pre-processing)
  - [Exploratory Data Analysis](#exploratory-data-analysis)
  - [Recommendation Techniques](#recommendation-techniques)
    - [User-based Collaborative Filtering](#user-based-collaborative-filtering)
    - [Item-based Collaborative Filtering](#item-based-collaborative-filtering)
    - [Content-based Filtering](#content-based-filtering)
    - [ALS (Alternating Least Squares)](#als-alternating-least-squares)
    - [Hybrid Recommendation System](#hybrid-recommendation-system)
  - [Model Evaluation](#model-evaluation)
- [Conclusion](#conclusion)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Introduction
iPrint aims to reduce revenue leakage by personalizing user tastes and introducing new content daily on the application's homepage. We will assess these recommendations by tracking user interactions with the content. If a user clicks on a news item, we will recommend similar news items at the bottom of the page to further refine user interests.

## Problem Statement
The goal is to build a recommendation system that:
1. Recommends the top 10 relevant articles to users at the start of the day.
2. Recommends the top 10 similar articles based on the articles clicked by the user.

## Data Description
- **consumer_interactions**: Contains interaction types (content_followed, content_commented_on, content_saved, content_liked, content_watched).
- **platform_content**: Contains metadata about the articles including their language and keywords.

## Approach
### Data Pre-processing
- Impute rating values based on interaction types with weightage: content_followed > content_commented_on > content_saved > content_liked > content_watched.
- Filter English articles from `platform_content`.

### Exploratory Data Analysis
- Analyze the distribution of interaction types, consumer location, producer location, item type, etc.
- Identify the most common language and most popular consumer country.

### Recommendation Techniques

#### User-based Collaborative Filtering
1. Create a user-item matrix using rating values.
2. Compute the user-similarity matrix using a similarity measure.
3. Generate predicted ratings for user-item pairs.

#### Item-based Collaborative Filtering
1. Compute the item-similarity matrix using a similarity measure.
2. Recommend top 10 similar items based on similarity scores.

#### Content-based Filtering
1. Analyze the ‘keywords’ feature using text processing.
2. Recommend items based on TF-IDF scores.

#### ALS (Alternating Least Squares)
1. Create Compressed Sparse user-item and item-user matrices.
2. Train the ALS model and generate recommendations.
3. Experiment with hyperparameters for optimization.

#### Hybrid Recommendation System
1. Normalize scores from content and collaborative filtering.
2. Combine with appropriate weightage to form a hybrid model.
3. Experiment with various hybrid models (e.g., Content+Item-based, ALS+Item-based).

### Model Evaluation
- Evaluate using metrics such as RMSE, MAE, and Recall@k.
- Recommend evaluation techniques for the second problem statement, exploring methods for online evaluation.
![image](https://github.com/SuryaBandari247/New-Recommendation-System/assets/128714777/c36bddc1-c52c-41f8-b318-651d37048f8e)
![image](https://github.com/SuryaBandari247/New-Recommendation-System/assets/128714777/aff30b1c-4069-4774-8bd3-da68fe6562a3)

## Conclusion
After conducting an in-depth evaluation, we have arrived at recommendations tailored to address two distinct problem statements within our application's functionality.

Firstly, regarding the task of suggesting the most relevant articles to users upon their initial app visit each day, we propose employing either User-based Collaborative Filtering or a Hybrid approach incorporating Alternating Least Squares (ALS) with User-based filtering. 
These methods leverage user behavior and preferences to generate personalized recommendations, ensuring that the user is presented with content aligned with their interests and tastes.

Secondly, for the objective of recommending articles similar to those previously clicked by the user, our recommendation leans towards the utilization of a Hybrid ALS model combined with Content-based filtering techniques. 
By combining ALS with content-based filtering, we can effectively capture both user preferences and content similarity, thereby enhancing the accuracy and relevance of the recommended articles. 
This approach ensures that users are provided with a best selection of news articles that closely align with their interaction history and interests, thereby enriching their overall experience within the application.
