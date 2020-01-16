# DonorsChoose.org Application Screening
## *Can you predict whether teachers' project proposals are accepted?*


![Image description](donorschoose_logo.png) <br />

## Task 

Donorschoose.org receives project proposals from thousands of teachers who need funding for their classroom projects. The Donorchoose.org volunteers need to manually evaluate all the received proposals to decide whether to approve the project or not. However, such a process is not scalable especially when Donorschoose.org expects to receive over 500,000 applications next year. 

The goal of the project is to predict whether or not a DonorsChoose.org project proposal submitted by a teacher will be approved, using the text of project descriptions as well as additional metadata about the project, teacher, and school. DonorsChoose.org can then use this information to identify projects most likely to need further review before approval. 

## Evaluation 

The models were evaluated using the Area Under the Receiver Operating Characteristic curve (AU-ROC or AUC).

## Approach

Datasource: https://www.kaggle.com/c/donorschoose-application-screening/data

Features from text: 
1) Bag of words
2) TF-IDF 
3) Glove vectors 

Models Built:
1) KNN using the following features 
+-------------------------+-------------+-----------------+-------+<br />
|        Vectorizer       |    Model    | Hyper parameter |  AUC  |<br />
+-------------------------+-------------+-----------------+-------+<br />
|           BOW           |    Brute    |        51       | 0.598 |<br />
|          TFIDF          |    Brute    |        41       | 0.540 |<br />
|       AvgWord2Vec       |    Brute    |        41       | 0.576 |<br />
| TFIDF weighted Word2Vec |    Brute    |        31       | 0.594 |<br />
|          TFIDF          | SelectKBest |        51       | 0.531 |<br />
+-------------------------+-------------+-----------------+-------+<br />
2) Logistic Regression 
+------------------------------------+-------+-----------------+--------+
|             Vectorizer             | Model | Hyper parameter |  AUC   |
+------------------------------------+-------+-----------------+--------+
|                BOW                 | Brute |      0.009      | 0.721  |
|               TFIDF                | Brute |     0.000155    | 0.706  |
|            AvgWord2Vec             | Brute |     0.00055     | 0.6788 |
|      TFIDF weighted Word2Vec       | Brute |      0.0008     | 0.687  |
| Categorical and Numerical features | Brute |      0.236      |  0.60  |
+------------------------------------+-------+-----------------+--------+

3) Naive Bayes
+------------+-------+-----------------+--------------------+
| Vectorizer | Model | Hyper parameter |        AUC         |
+------------+-------+-----------------+--------------------+
|    BOW     | Brute |       0.1       | 0.691536613436315  |
|   TFIDF    | Brute |       0.31      | 0.6624800593234719 |
+------------+-------+-----------------+--------------------+

## Results 

