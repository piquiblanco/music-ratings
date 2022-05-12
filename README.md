# music-ratings

The project uses data on ratings which I've been giving out to music I listen to. Ratings from compatible users found on Rateyourmusic.com are also utilized, as well as some metadata (genre, release year).

## Project goal

The goal of this project is to answer five questions:
- Q1 - What part of my music taste can be described and predicted?
- Q2 - What are my favorite genres?
- Q3 - What are my favorite decades/periods?
- Q4 - What are some albums that I should've liked according to a well-trained model, but didn't?
- Q5 - What are some albums liked by me that a well trained-model expected me to dislike?

## CRISP-DM process phases - brief overview
### 1. Problem understanding
The project focuses on attempting to predict ratings which I give out to music I listened to. This can be predicted to some extend using relevant data, but as the topic of the analysis are subjective experience, we shouldn't expect to be able to predict it completely. Anything that explains some of the variance and enables inference will be satisfying.
### 2. Data understanding
Three datasets are available: `my_ratings`, `user_ratings`, and `metadata`. Dataset `my_ratings` is the most straightforward and contains the variable we'll try to predict (the album score); `user_ratings` contains null values which have to be handled appropriately, and `metadata` contains text data which have to be split and analyzed before we'll able to use them in the model.
### 3. Data preparation
Challenges identified in step 2 were addressed in this step. New variables were created based on `metadata` dataset. Additionally, a discrepancy between dataset domain between `my_ratings` and `user_ratings` was addressed: each of the dataframes contained some rows which the other one didn't have.
### 4. Modeling
Data was subject to leave-one-out crossvalidation, with ridge regressions trained for each iteration. Three classes of models were analyzed: based on user ratings, based on metadata, and based on all available data.
### 5. Evaluation
Models described in step 4 were subject to evaluation based on two metrics. R-squared and root mean squared error. The best model achieved R-squared of over 20%, which was my initial target. (Answer to Q1)
### 6. Deployment
This step was in the scope of the project, as the model built served an inferential purpose. Coefficient of final model were analyzed to see which independent variables describe my ratings (answers to Q2, Q3). Finally, predictions were analyzed with respect to biggest differences between model predictions and real ratings (answers to Q4, Q5).
