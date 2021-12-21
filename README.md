# Machine Learning Final Project

## Introduction

For this project we wanted to see how we can apply what we have learnt in class to a real world problem.
We ended up choosing music genre classification because it is quite a relevant task in industry where companies like Spotify and Apple Music are trying to automatically classify songs into various genres.

We decided to use a project from ---(Allan) hackathon where a basic Logistic Regression model was used to classify songs. The dataset consisted of ---(Allan) songs from the following genres:

- pop
- etc(Allan)

The dataset also had the following metrics and labels for each song:

- Artist name
- etc(Allan)

The baseline we used was the accuracy which was --- (Allan) from the hackathon using a Logistic Regression model. We decided to experiment with different models and see how best we can improve this accuracy and the factors that affect it based on what we learnt in class.

## Preprocessing

The first experiment we conducted was using the Logistic Regression Model but with some more data preprocessing. We got rid of the "Artist name" and "Track name" columns from the dataset and also removed rows with all NaN values.

The we separated the feature matrix from the output vector which contains the genre. The dataset was split into training and testing with an 4:1 split.

We further scaled the data using Standard Scaler by fitting it on the training dataset and transforming both the training and test data.

## Logistic Regression

For this experiment, the Logistic Regression model from sklearn was used along with K-fold cross validation to figure out the best penalty with l2 regularization. We used a list of penalities:

```
ptest = [0.0001, 0.001, 0.01, 0.1, 1.0]
```

The best penatly was found to be 1.0 with an average accuracy of 49% hence most of the features being used was important and there was not much need to penalize them.

With this we conducted one more test to see which features were the most important and how many we needed to maintain the same accuracy. Feature selection with recursive feature elimination was used (RFE) which produces these results for the top features:

1. duration_in min/ms
2. energy
3. speechiness
4. acousticness
5. instrumentalness
6. danceability
7. valence
8. Popularity
9. loudness
10. mode
11. liveness
12. tempo
13. key
14. time_signature

By testing using the top feature and included the rest, we found that we needed the first 13 to achieve a high enough accuracy (50%) as can be seen in the notebook(add link to notebook here).
