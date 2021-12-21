# Machine Learning Final Project

## Introduction

For this project we wanted to see how we can apply what we have learnt in class to a real world problem.
We ended up choosing music genre classification because it is quite a relevant task in industry where companies like Spotify and Apple Music are trying to automatically classify songs into various genres.

We decided to use a project from kaggle where a basic Logistic Regression model was used to classify songs in a submission for a hackathon competition. The dataset consisted of 15129 songs from the following genres:

-   Pop
-   Acoustic/Folk
-   Alt Music
-   Blues
-   Bollywood
-   Country
-   Hip Hop
-   Indie Alt
-   Instrumental
-   Metal

The dataset also had the following metrics and labels for each song:

-   Artist name
-   Popularity
-   Danceability
-   Energy
-   Key
-   Loudness
-   Mode
-   Speechiness
-   Acousticness

The baseline we used was the accuracy which was 49% from the hackathon using a Logistic Regression model. We decided to experiment with different models and see how best we can improve this accuracy and the factors that affect it based on what we learnt in class.

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

## Neural Network

A nerual network was then implemented, utilizing two hidden layers, and one dropout layer. Multiple rounds of testing was done in order to achieve the most effective neural network. The first was to identify the most appropriate number of hidden units. Using other academic papers, various approaches were applied, and hidden units from a range of 10 - 350 were all tested.

According various academic papers, although context of the case study could lead to vastly different results, the most appropriate range was likely to be found within the range of the number of inputs and number of outputs + number of inputs. This ended up being the case, as the most effective number of hidden units was 34.

With only two hidden layers, and no dropout layer, the highest accuracy acchieved was 54.8%. When dropout layers were incorporated, it was found that accuracies in fact decreased by a consistent 2%. Only one dropout layer gave the highest accuracy at a value of 0.5 between the two hidden layers (in comparison to multiple dropout layers). However, it was clear that in this case study, zero dropout layers was more effective.

In the document, it can be seen that some data cleaning is implemented. One of the 14 features is in fact dropped, as a quick investigation found that it was not providing significant results in the final classification. Although this was the case for an SVM and for Log Reg, the NN performed better when all 14 features were incorporated. This makes sense, as a NN is more effective with more complex systems.
