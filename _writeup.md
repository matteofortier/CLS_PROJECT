# Classification Model for Games

*Matteo Fortier*

## Abstract

The goal of this project was to explore wheter classifcation models could be used to identify games with high average playtime. This is important to investigate from the point of view of Epic Games, a store currently taking the approach of aquiring exclusives in order to become the industry leader. Public data available from the Steam Store API and Steam Spy API was used to formulate my target and feature variables. The two data sources were combined to expand the features available for each observation, leveraging both numerical and categorical features. XGBoost and Random Forest were explored as the primary classifiers for the project. The model was iteratively improved using pipelines to streamline the process. 

## Design

The Epic Games Store had an average of 56 million monthly active users in 2020, while Steam had 120 million monthly active users ([Source](https://backlinko.com/steam-users)). As a result, the company has been following an "aggressive pursuit model", spending 1 billion dollars on securing exclusive games in 2019 ([Source](https://www.pcgamer.com/uk/epic-games-has-spent-at-least-dollar1-billion-on-exclusives/)). While the model has successfully gathered its current users, the enormous spending is unsustainable; Epic's largest source of revenue, Fortnite, is diminishing, and the store itself has yet to turn a profit ([Source](https://www.ign.com/articles/fortnite-made-9-billion-in-two-years-while-epic-games-store-has-yet-to-turn-a-profit)). Thus Epic plans to decrease the number of exclusives it plans to secure each year, from 52 in 2021 to 36 in 2022. 

Hence, knowing which games are most likely to grow Epic's platform is valuable, seeing as they cannot continue buying every game that exists. Epic would prioritise which games they obtain exclusive rights to based on their predicted engagment.

## Data

Two seperate datasets were used for the project. The Steam Store API data and Steam Spy API data. The two were combined on game's appid. The combined dataset contains 40,000+ games with 29 raw features, the majority of which are categorical. Many categorical features were actually multilabel features, thus multi-label encoding had to be engineered for these features. Some numeric features also had missing observations and thus null imputing also had to be done. One of the more powerful features was 'tags', a multi -label categorical feature with 500 unique labels. Dimensionality reduction algorithms was used to preprocess this feature. Other features were engineered, some carefully considering the time  of the observation in order to minimise data bleed. 

## Algorithms

***Feature Engineering***

1. Converting categorical features to one hot encodings using column transformer
2. Converting multi-label categorical features to multi hot encodings using column transformer + multihotencoder
3. Getting the average hours/owners/recommendations of a publisher for all previous observations for a given observation.
4. Getting the average hours/owners/recommendations of a **developer** for all previous observations for a given observation.
5. Pre-processing large multi hot encodings using dimensionality reduction algorithms such as PCA
6. Converting some large multi hot encodings into counts

***Models***

With prediction priority over interpretability in mind, more performant models were considered.

These models include XGBoost and Random Forest.

For XGBoost the best evaluation metrics were 'auc' and 'pr_auc'.

***Model Evaluation and Selection***

Within the context of the problem, falsely selecting a bad game costs more than not selecting a good game. As such, precision was favoured slightly over recall, and thus f0.6 was the main metric to compare models against, along with ROC AUC for predictive potential.

The dataset was split into train/test with the holdout size being 20% (StratifiedSplit was used to keep distribution of target variable). The train set was always cross validated to reduce overfitting using GridSearchCV and StratifiedKSplit. 

Hyperparameter tuning was simply done in through the pipeline using GridSearchCV accompanied with a param grid. This allowed for the automatic tuning of important hyper-parameters such as class weights, evaluation metrics, max tree depth, max features, etc. 

## Communication

The project used powerpoint for the presentation and the python visualisation libraries for the visuals. 

roc_curve and precision_recall_curve were used from the metrics library to produce the plots.