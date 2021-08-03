### MVP:

The focus of the project was to explore whether  high engagement games be predicted using a classification model.

A baseline model was created using a subset of the features avaialble on the dataset using a random forest classifier. Genres (categorical), Categories (categorical), Platforms (categorical) and Owners (numerical) were initially used to predict whether an hours played threshold could be passed. class_weights were also employed. Here is a confusion matrix representing the results of the initial baseline model:

|                       | Predicted Negative | Predicted Positive |
| --------------------- | ------------------ | ------------------ |
| **Actually Negative** | 8121               | 2                  |
| **Actually Positive** | 222                | 13                 |

```
precision:  0.8666666666666667
recall:  0.05531914893617021
f1 : 0.10400000000000001
```

While the model has a high precision score, it's recall score is poor. This suggests the model is really cautious in classifying positive observations. Features with more signal can be engineered, especially regarding developers and publishers of games, to potentially improve the model. Tag data can also be used to provide more granular descriptions of games' content. XGBoost can also be considered as a potential alternative model. 