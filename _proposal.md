### Project Proposal: Classifying Most Played Steam Games

*Matteo Fortier*
**Framing Question:** Which games are played the most on the Steam store?

Can high engagement games be predicted using a classification model?

**Purpose and Need:** The Epic Games Store had an average of 56 million monthly active users in 2020, while Steam had 120 million monthly active users ([Source](https://backlinko.com/steam-users)). As a result, the company has been following an "aggressive pursuit model", spending 1 billion dollars on securing exclusive games in 2019 ([Source](https://www.pcgamer.com/uk/epic-games-has-spent-at-least-dollar1-billion-on-exclusives/)). While the model has successfully gathered its current users, the enormous spending is unsustainable; Epic's largest source of revenue, Fortnite, is diminishing, and the store itself has yet to turn a profit ([Source](https://www.ign.com/articles/fortnite-made-9-billion-in-two-years-while-epic-games-store-has-yet-to-turn-a-profit)). Thus Epic plans to decrease the number of exclusives it plans to secure each year, from 52 in 2021 to 36 in 2022. 

Hence, knowing which games are most likely to grow Epic's platform is valuable, seeing as they cannot continue buying every game that exists. Epic would prioritise which games they obtain exclusive rights to based on their predicted engagment.

**Data Description:**

Steam Store API and Steam Spy API data will be used. 

The data includes information on engagement statistics such as average and median hours played in the past two weeks/all time.

 The data also includes various categorical and numerical features such as developer, publisher, genres/tags, price, rating. 

The data has 44000 observations. 

**Tools:**

- Requests and Pandas libraries for data ingestion from APIs
- SQLite database for data storage
- SciKit and Pandas libraries for classification modelling (logistic regression, random forest, decision trees, ...)
- Matplotlib and seaborn for visualisations, potentially tableau to illustrate certain findings.

**MVP Goal:**

Baseline classification model, using a few features. Potentially a logistic regression model.