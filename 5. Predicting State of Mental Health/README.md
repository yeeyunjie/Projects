Capstone project: Identify respondents that avoid seeking mental help
---

### Problem Statement
---
The ongoing Household Pulse Survey conducted in the States aims to measure household experiences during the coronvarius pandemic. This unprecendented spread of disease is predicted to have a long-tail effect on the mental health of people. Moreover, the lack of mental heath literacy/awareness has discouraged people from seeking the help they need. In order to identify this susceptible group of people as well as to understand and quantify importance of factors that drive such a vulnerability/resistance to seeking mental aid, I aim to build two models to meet two different objectives. One is a binary classification **ExtraTrees Classifier model** to predict the development of avoidance behaviours with regards to seeking mental health therapy and a second **Logistic Regression** inference model to identify the top predictor features given the wide range of variables present which provides a holistic overview of a person's livelihood. Understanding these features would aid in making well-informed recommendations to better tackle the root causes of such a tendency. The performances of these models would be evaluated by **ROC-AUC** and **recall** scores. 

### Executive Summary
---
Prior to COVID-19, Mental Health America(MHA) has reported an increase in the number of mental health disorders from 2017-2018 where an additional 1.5million people suffered from mental health distress. Moreover, reports have shown that these health needs are often unmet, with 60% of youths and 23.6% of adults with major depression not receiving adequate treatments even in states with highly accessible healthcare. The declaration of a national state of emergency for COVID-19 on March 13 has only exacerbated this phenomenon. Mental Health America(MHA) has reported that there is a 634% and 873% increase in the number of people who underwent online anxiety and depression screening tests respectively on the MHA portal from Janaury to September 2020. Among these respondents, 8/10 of them were scored with moderate to severe symptoms since the declaration of the covid pandemic. Therefore there is an alarming trend in the number of people developing mental health disorders.There is now an increasing need to destigmatize mental health and to provide early interventions before associated problems manifest. <br> 

**Direction of the project** <br>
The goal is to build two models, one to identify susceptible respondents to developing mental health issues and the other to identify important predictor features that strongly correlates with such a tendency.The metrics used to evaluate the models' performances are ROC-AUC and recall scores. With these two models, I aim to provide well-informed suggestions to stateboards and mental health institutes on where to focus and channel resources to curb underlying root causes of such mental distress. Data used is collected from the Household Pulse Survey conducted by United States Census Bureau which is a holisitic questionnaire that measures social,economical and physical impact of COVID on a person's livelihood.

**Findings - Data Analysis** <br>
A logistic regression model used identified the frequency of feeling down/sad/hopeless(`DOWN` variable), frequency of feeling anxious(`ANXIOUS`) and age(`TBIRTH_YEAR`) as the top few predictor variables that correlates with a resistance to seeking mental health aid(`MH_NOTGET`). <br>

- #### `DOWN` and `ANXIOUS`
There is a positive correlation with `DOWN` and `ANXIOUS` and `MH_NOTGET` where respondents who experience persistent feelings of sadness and anxieties are more likely to be passive in seeking mental therapy.

- #### `TBIRTH_YEAR`
There is a positive correlation between `TBIRTH_YEAR` and `MH_NOTGET` as the younger population are more susceptible to developing such an inclination as compared to the older generation.


**Findings - Data Modeling** <br>
An optimized ExtraTrees Classifier was selected as the final model due to its reduced bias and variance errors as compared to the other models. Based on this model, we could also re-evaluate the false positives generated where respondents exhibited signs of refusing mental help but they have indicated otherwise.<br>


### Risks and Assumptions
--- 
The dataset consists of a set of questionaries which are heavily subjected to response bias given that these survey questions are answered voluntarily. Therefore, the responses are highly influenced by experimental conditions such as phrasing of questions in surveys, length of survey and intentions of a respondent. Moreover, since this is an online survey, this would disregard respondents such as those who lack access to internet services and thus would not be reflective of these groups of people. However, collection of data from such an online avenue would allow for a quicker collation of results especially given that there is an existing increase in people seeking mental help online and thus appropriate interventions can be implemented as soon as possible. Lastly, models built would not allow help to predict future occurrences but also to re-assess the sentiments of the current respondents' which could potentially identify those who are unaware of an existing mental condition.

### Methodology
---
#### Import Data
1) pulse2020_puf_13.csv (109,051 rows) from 2020-08-19 to 2020-08-31<br>
2) pulse2020_puf_14.csv (110,019 rows) from 2020-09-02 to 2020-09-14<br>
#### Data Cleaning and Visualization
1) Drop redundant columns (Date, Latitude, Longitude, Block, Street, Address and some weather
2) Removal of duplicates <br>
3) Implementing imputation <br>
4) Removal of correlated features <br>
#### Feature Engineering and Selection
1) Creation of new feature from existing variables(`HOUSEPAY`)
2) Ordinal encoding for ordinal features
3) One hot encoding for nominal features
4) Chi square tests to select for dependent categorical variables
5) Principal Component Analysis(PCA) for dimensionality reduction
#### Modelling
1) Applied Train-test-split on train dataset
2) Applied Standard Scaler on X_train and transform X_test
3) Applied RandomUnderSampler on train set(method to undersample majority class)
4) Tune hyperparameters using GridSearchCV
5) Generate Predictions

### Data Dictionary
---

|Feature|Type|Dataset|Description|
|:---|:---|:---|:---|
|EST_ST|int|cleaned_data_week_13.csv/cleaned_data_week_14.csv|State|
|TBIRTH_YEAR|int|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Year of Birth|
|EGENDER|int|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Gender|
|RHISPANIC|int|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Hispanic Origin|
|RRACE|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Race|
|EEDUC|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Educational attainment|
|MS|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Marital Status|
|WRKLOSS|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Recent household job loss|
|EXPCTLOSS|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Expect household job loss|
|ANYWORK|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Employment status for last 7 days|
|UI_APPLY|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Applied for Unemployment Insurance(UI)|
|SSA_RECV|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|State of receiving Social Security Benefits|
|EXPNS_DIF|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Difficult with expenses|
|WHYCHNGD1|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to shopping places restrictions|
|WHYCHNGD2|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to re-opening/extension of stores'operation duration|
|WHYCHNGD3|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to avoidance of crowded/high-risk public areas|
|WHYCHNGD4|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to lack of avoidance of crowded/high-risk public areas|
|WHYCHNGD5|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to loss of income|
|WHYCHNGD6|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to increase in income|
|WHYCHNGD7|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to concerns about unemployment/reduced work hours|
|WHYCHNGD8|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to lack of concerns about unemployment/reduced work hours|
|WHYCHNGD9|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to working from home/teleworking|
|WHYCHNGD10|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to resumed working onsite at workplace|
|WHYCHNGD11|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to concerns about economy|
|WHYCHNGD12|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to lack of concerns about economy|
|WHYCHNGD13|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Change in household spending due to other reasons|
|SPNDSRC1|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Similar income sources as pre-covid|
|SPNDSRC2|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - credit cards/loans|
|SPNDSRC3|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Money from savings/selling assets|
|SPNDSRC4|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Borrow from friends/family|
|SPNDSRC5|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Unemployment Insurance(UI) benefit payments|
|SPNDSRC6|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Stimulus(economic impact) payment|
|SPNDSRC7|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Money saved from deferred/forgiven payments|
|SPNDSRC8|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Source of spending needs - Supplemental Nutrition Assistance Program(SNAP)|
|FREEFOOD|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Retrival of free groceries/meal in last 7 days|
|WHEREFREE1|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/meal - School programmes|
|WHEREFREE2|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/meal - Food pantry/food bank|
|WHEREFREE3|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/Home delivered meal service|
|WHEREFREE4|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/meal - Religious organizations|
|WHEREFREE5|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/Shelter/soup kitchen|
|WHEREFREE6|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/meal - Other community programmes|
|WHEREFREE7|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Sources of free groceries/meal - Family,friends,neighbors|
|SNAP_YN|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Subscription to Supplemental Nutrition Assistance Program(SNAP)|
|TSPNDFOOD|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Househol money spent in last 7 days on prepared meals|
|FOODCONF|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Food sufficiency confidence for next 4 weeks|
|HLTHSTATUS|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|General health status|
|ANXIOUS|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Frequency of anxiety over previous 7 days|
|DOWN|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Frequency of feeling depressed over previous 7 days|
|PRIVHLTH|int|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Ownership of private health insurance|
|PUBHLTH|int|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Ownership of public health insurance|
|DELAY|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Delay of medical care in due to pandemic|
|PRESCRIPT|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Taking prescription medicine for mental health|
|DELAY|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Delay of medical care in due to pandemic|
|MH_SVCS|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Receive professional mental health services|
|MH_NOTGET|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Require mental help but did not get it|
|TENURE|obj|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Status of housing ownership(owned/rented)|
|PSPLANS1|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Type of post-sec programme expected to take - Diploma/occupational training|
|PSPLANS2|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Type of post-sec programme expected to take - Associate's degree programme|
|PSPLANS3|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Type of post-sec programme expected to take - Bachelor's degree programme|
|PSPLANS4|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Type of post-sec programme expected to take - Graduate degree programme|
|PSPLANS5|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Type of post-sec programme expected to take - Other credential programme|
|PSPLANS6|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Type of post-sec programme expected to take - Classes that are not part of credential programmes|
|PSWHYCHG1|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Had coronavirus/concerns about getting the virus|
|PSWHYCHG2|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Caring for someone who coronavirus|
|PSWHYCHG3|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Caring for others whose care arrangements are disrupted|
|PSWHYCHG4|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Institution changed content/format of classes|
|PSWHYCHG5|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Changes to financial aid|
|PSWHYCHG6|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - changes to campus life|
|PSWHYCHG7|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Uncertainty about how classes/programmes might change|
|PSWHYCHG8|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Unable to afford classes/educational expenses because of income changes due to pandemic|
|PSWHYCHG9|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Reasons for post-sec educational plans change - Other reasons related to the pandemic|
|INCOME|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Total household income|
|FOODSUF|float|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Food sufficiency prior to March 13|
|HOUSEPAY|object|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Abiltiy to support housing payments|
|INSURED|object|cleaned_data_week_13.csv/cleaned_data_week_14.csv|Presence of insurance|

### Findings
---
1) `DOWN` and `ANXIOUS` 
- There is a strong correlation between greater frequency of feeling down/anxious and avoidance of seeking mental health therapy. This correlation is apparent in Oregon and Colorado. Whereas in North Dakota and South Dakota where frequency of feeling down/anxious is lower, avoidance behaviours are less prevalent in those states

2) `TBIRTH_YEAR`
- Age has a considerable influence on the development of avoidance behaviours as it seems to be more common among the younger population than the older ones. The mean age of respondents that do not exhibit such behaviour is 52 while the mean age of respondents that do is 42. According to external research, this average value also happens to be within the age range(15-44) which are the most susceptible to depression.


#### Best Model
<u>Models trained:</u><br>
- Logistic Regression
- K Nearest Neighbours, 
- Random Forest Classifier 
- Extra Trees Classifier 
- XGBoost Classifier
- Neural Nets

Through training of 8 different classification models, we have selected Logistic Regression for inferential analysis and ExtraTrees Classifier as our predictive model. 

|Model| ROC-AUC score | Recall | Best Parameters |
|----------|------------------------------|
| Logistic Regression | 0.790 | 0.802 | C: 0.01, penalty: l2 |
| ExtraTrees Classifier | 0.770 | 0.856 | class_weight: balanced, max_depth: 40, max_features: auto, min_samples_leaf: 20, n_estimators: 150 | 


#### Limitations of models
**1) Self-reported assessment of mental health conditions:** <br>
Since data collected is heavily subjected to the biases of respondents especially with regards to mental health, models developed should only be used as a reference. Evaluation of a mental health condition should be done by a certified professional and ideally through objective measurements. One example would be on a recent study using MRI scans which have identified a promising biomarker involving the blood-brain barrier in patients with major depression. However, such experiments are still in their early stages and thus small in scale so more data has to be collected before machine learning models can be utilized to improve detection. 

**2) Imbalanced classes:** <br>
Undersampling was done to randomly reduce the number of rows in the majority class but doing so would disregard important features present in the training set. Therefore, more data needs to be collected to further improve on the performances of such models. 


### Conclusion 
**1) Logistic regression for feature importance**
The logistic regression is advantageous in quantifying the strength and direction of each feature in determining the target variable unlike the ExtraTrees and RandomForests. Feature importances identified by the ensemble learning methods are not interpretable in helping to generate predictions or for analysis. Even though the ROC-AUC and recall scores of logistic regression are lower than that of the ensemble methods, there is less overfitting in logistic regression and thus able to generalize better to unseen data.

**2) ExtraTrees Classifier for predictions**
The model chosen to for predictive purposes would be the ExtraTrees Classifier with its optimal tuned hyperparameters. Although most of the models have shown comparable ROC-AUC and recall scores, this classifier exhibited an optimal balance of bias-variance tradeoff and thus it is best able to generalize to unseen data. Even though the performance of RandomForests was similar to the ExtraTrees, it was time consuming to run the former and thus deployment of ExtraTrees would be computationally efficient.

### Recommendations
Based on the features identified to have strong correlations with our target variable(`DOWN`,`ANXIOUS`,`TBIRTH_YEAR`), they would be the deciding factors for the states chosen where these models could be implemented. This would help to narrow our target population and provide a greater understanding of the magnitude of spread of mental health disorders when models are fed with state-specific data. Therefore, local health departments can make well-informed decisions on resource allocation according to the needs of different states <br>

**1) Implement models in a state that requires immediate aid - Oregon:** 
Before these models are used on a larger scale, it would be more effective to deploy the model in a state that requires urgent intervention. One such example would be Oregon as it has marked the checkbox on high `DOWN` and `ANXIOUS` values and a comparatively younger population.

**2) Implement models in states that show similar characteristics - Utah, Illinois:**
These states have been identified to have `DOWN` and `ANXIOUS` on the higher end of the scale and also relatively younger populations.
