# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & Classification

### Problem Statement
Billion-dollar sports league such as NBA and EPL are huge markets for businesses to tap on given the extent of reach and wealth generated. With such a large consumer market, it would be productive to track the current sentiments of our consumers and leverage on their interests to provide business ideas to our clients. Our primary stackholders are sports companies including retailers and providers of sports services(bootcamps/clinics) that are looking for potential marketing investment opporunities by analyzing the current sentiments of sports fans. Our secondary stackholders are digital marketing companies that searching for avenues to better improve communication with their consumers. Therefore, by analyzing 2 of the most popular sports, basketball and soccer, we could better understand our potential consumers' behaviours and preferrences before we invest in specific business strategies. To achieve maximum profit, we aim to develop a model that correctly predicts the category that a new unseen post belongs to and from this classification, we could further explore the interests of our consumers by analyzing the posts that these words belong to. We quantify the performance of our model using the accuracy and F1 score metric across all potential models. Ultimately, the use of Term Frequency — Inverse Document Frequency(TF-IDF) technique was more appropriate given the dominance of several words as it places greater emphasis on unique words while the implementation of a Logistic Regression model helped us to quantify the influence of words on the differentiating power of our model. This model would be beneficial even to businesses without prior knowledge in the sports industry and to be constantly updated on the current trend.

### Executive Summary
The provision of Application Programming Interfaces(APIs) as an alternative to web scrapping has granted unpredecented access and retrival of large amounts of data in an automated fashion. One such provider is Reddit and through the exploitation of such a powerful tool, we would be able to collect,organize and draw insights that distinguishes posts from 2 particular subreddits on basketball and soccer. After the removal of redundant tokens/words that provide no discriminatory value such as website links, stopwords and punctuations, there are a few common words that appear frequently. Interestingly, through the analysis of the subreddits, it was discovered that users on basketball subreddits are more interested in understanding and improving on the technical aspects of the sport while users on soccer subreddts are more invested in engaging in post-match discussions and also about their favourite teams. In addition, the model is highly accurate in predicting the category that each post belongs to given the high accuracy scores in both train and test set as well as the F1 scores which determines the accuracy of our predictions. This model emphasises on the use of bigrams to decipher the categories of posts due to the value adding aspects as compared to a unigram. With such a high predictive power, this model serves as a catalyst for building a strong connection between our clients and their desired consumers.

### Data Dictionary
#### Data Dictionary for `df_bball`: <br>

|Feature|Type|Dataset|Description|
|---|---|---|---|
|posts|object|basketball|basketball posts| 
|is_basketball|int|basketball|1: Basketball, 0: Soccer| 

#### Data Dictionary for `df_s`: <br>

|Feature|Type|Dataset|Description|
|---|---|---|---|
|posts|object|soccer|soccer posts| 
|is_basketball|int|soccer|1: Basketball, 0: Soccer| 

#### Data Dictionary for `df`: <br>

|Feature|Type|Dataset|Description|
|---|---|---|---|
|posts|object|combined_df|basketball or soccer posts| 
|is_basketball|int|combined_df|1: Basketball, 0: Soccer| 

### Conclusion/Recommendations
Based on the findings, we can draw several conclusions: <br>

1) **Benefits of determining important tokens:** <br>
Based on the analysis of data collected from each subreddit, the use of TfitVectorizer() has given us insight on the current sentiments of the respective reddit users. The exploration of bigrams has uncover trends within each specific subgroup, namely seeking assistance with regards to the technical aspects of basketball as well as the prevalence of the high school bigram which could indicate a sparked interest in that particular group of consumers. Whereas within the soccer community, the high occurrence of of post thread and match thread suggest that users are more engaged in post match discussions and their interests lie in specific soccer teams. Such differing behaviours could provide an avenue for business ideas that cater specifically to a group of target consumers. Leveraging on a demand for assistance in basketball programs/clinics, sports academies could invest in advertizing their services on these platforms. Moreover, they could also extend their outreach through collaborations with schools as a more directed avenue.
Whereas for the soccer community, companies could invest in developing platforms where services such as provision of real time updates on games and soccer teams to cater to the large fanbase. Therefore, this model could provide actionable insights even for companies that are not in touch with the sports industry.

2) **Highly accurate predictive performance of model:** <br>

Summary of the accuracy scores from different models with their corresponding vectorizers and tuned parameters
| Model | Normalization technique | Vectorizer | Best Parameters | Train Set Accuracy | Test Set Accuracy | F1 Score |
| --- | --- | --- | --- | --- | --- | --- |
|Logistic Regression|Lemmatization|CountVectorizer|max_df: 0.1, max_features: 1500, min_df: 2, ngram_range:(2,2)|0.81047|0.88407|0.88955|
|Logistic Regression|Lemmatization|TF-IDF|max_df: 0.1, max_features: 1000, min_df: 2, ngram_range: (2, 2)|0.86492|0.83384|0.89130|   
|Naive Bayes|Lemmatization|TF-IDF|max_df: 0.1, max_features: 1500, min_df: 2, ngram_range: (2, 2)|0.8997|0.8565|0.90414|

Based on the table above, the Logistic regression model with a TF-IDF vectorizer would be the model of choice given a small margin of difference between the accuracy scores of train and test set. This is indicative of a model with low variance and a low chance of overfitting thus the model is able to generalize better to unseen data. In addition, the choice of the logistic regression over the naive bayes is due to the quantifiable influence of tokens on the output of the model. The larger the coefficients, the greater the importance of token on the output. Lastly, our model performs better than our baseline accuracy and thus would be worthwhile to implement


Limitations of model: <br>

1) **Difficulties in establishing independence between tokens**: <br>
Since the titles and content of posts are usually correlated, models such as Linear Regression and Naive Bayes which require features to be independent would not fare well in modelling text classification problems. Since establishing independence is an assumption for both logistic regression and naive bayes, multicollinearity between features would greatly affect the performance of our model.  In addition, discussion platforms are prone to repetitive and similar content given that the body of a post is an extension of its title, and thus would further reduce the model's performance in predicting categories of future posts. The possibility of **data leakage** is also high when rows in the data are similar even if train test split was done. 

2) **Problems with small datasets** <br>
The use of bigrams in our dataset significantly reduces the size of our input data and therefore our logistic regression model is very sensitive to outliers. Therefore, more data should be collected before they are fed as inputs into our model. Another way to deal with the small dataset would be to utilize the Naive Bayes model which copes well with a smaller dataset and with outliers.