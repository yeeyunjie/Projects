# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Testing, Statistical Summaries and Inference

### Problem Statement

With two different college exams available, SAT and ACT, we aim to locate, exploit factors that undermine preferences for the SAT test in particular and therefore provide recommendations to increase participation rate in a desired state. **New Mexico** would be our state of choice for investment given its promising potential in accepting SAT as the preferred college admissions exam which would be unravelled in the analysis below. 

### Executive Summary
The study of the participation rates and test results of both SAT and ACT test have unravelled the preferrences behind the selection of either of them as a college entrance exam. 
With a strong inverse correlation between SAT and ACT results as well as state policies that have been found to guide students' choices in their selection, New Mexico would be a promising
state to invest in given the lack of a mandated test, a low SAT participation rate and a comparatively lower ACT participation rate than other states. This impressionable education landscape 
has shown a great potential for room of growth in SAT participation rate and we can achieve such a goal through increasing the accessibility of SATs. 


#### Data Dictionary
##### `sat_2017_df`:
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|*object*|SAT_2017|State in US| 
|sat_participation_2017|*int*|sat_2017.csv|Percentage of participation(units in %)| 
|sat_evidence_based_reading_and_writing_2018|*int*|sat_2017.csv|Average score for evidence based reading and writing (range between 200 - 800)| 
|sat_math_2017|*int*|sat_2017.csv|Average score for math (range between 200 - 800)| 
|sat_total_2017|*int*|sat_2017.csv|Average total score (range between 400 - 1600)|

##### `sat_2018_df`:
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|*object*|sat_2018.csv|State in US| 
|sat_participation_2018|*int*|sat_2018.csv|Percentage of participation(units in %)| 
|sat_evidence_based_reading_and_writing_2018|*int*|sat_2018.csv|Average score for evidence based reading and writing (range between 200 - 800)| 
|sat_math_2018|*int*|sat_2018.csv|Average score for math (range between 200 - 800)| 
|sat_total_2018|*int*|sat_2018.csv|Average total score (range between 400 - 1600)|

##### `act_2017_df`: 
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|*object*|act_2017.csv|State in US| 
|act_participation_2017|*int*|act_2017.csv|Percentage of participation(units in %)| 
|act_english_2017|*int*|act_2017.csv|Average score for english (range between 1 - 36)| 
|act_math_2017|*int*|act_2017.csv|Average score for math (range between 1 - 36)| 
|act_reading_2017|*int*|act_2017.csv|Average score for reading (range between 1 - 36)|
|act_science_2017|*int*|act_2017.csv|Average score for science (range between 1 - 36)|
|act_composite_2017|*int*|act_2017.csv|Average score for science (range between 1 - 36)|

##### `act_2018_df`: 
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|*object*|act_2018.csv|State in US| 
|act_participation_2018|*int*|act_2018.csv|Percentage of participation(units in %)| 
|act_english_2018|*int*|act_2018.csv|Average score for english (range between 1 - 36)| 
|act_math_2018|*int*|act_2018.csv|Average score for math (range between 1 - 36)| 
|act_reading_2018|*int*|act_2018.csv|Average score for reading (range between 1 - 36)|
|act_science_2018|*int*|act_2018.csv|Average score for science (range between 1 - 36)|
|act_composite_2018|*int*|act_2018.csv|Average score for science (range between 1 - 36)|

##### `final`:
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|*object*|SAT_2017|State in US| 
|sat_participation_2017|*int*|sat_2017.csv|Percentage of participation(units in %)| 
|sat_evidence_based_reading_and_writing_2018|*int*|sat_2017.csv|Average score for evidence based reading and writing (range between 200 - 800)| 
|sat_math_2017|*int*|sat_2017.csv|Average score for math (range between 200 - 800)| 
|sat_total_2017|*int*|sat_2017.csv|Average total score (range between 400 - 1600)|
|act_participation_2017|*int*|act_2017.csv|Percentage of participation(units in %)| 
|act_english_2017|*float*|act_2017.csv|Average score for english (range between 1 - 36)| 
|act_math_2017|*float*|act_2017.csv|Average score for math (range between 1 - 36)| 
|act_reading_2017|*float*|act_2017.csv|Average score for reading (range between 1 - 36)|
|act_science_2017|*float*|act_2017.csv|Average score for science (range between 1 - 36)|
|act_composite_2017|*float*|act_2017.csv|Average score for science (range between 1 - 36)|
|act_participation_2018|*int*|act_2018.csv|Percentage of participation(units in %)| 
|act_english_2018|*float*|act_2018.csv|Average score for english (range between 1 - 36)| 
|act_math_2018|*float*|act_2018.csv|Average score for math (range between 1 - 36)| 
|act_reading_2018|*float*|act_2018.csv|Average score for reading (range between 1 - 36)|
|act_science_2018|*float*|act_2018.csv|Average score for science (range between 1 - 36)|
|act_composite_2018|*float*|act_2018.csv|Average score for science (range between 1 - 36)|
|act_participation_2018|*int*|act_2018.csv|Percentage of participation(units in %)| 
|act_english_2018|*float*|act_2018.csv|Average score for english (range between 1 - 36)| 
|act_math_2018|*float*|act_2018.csv|Average score for math (range between 1 - 36)| 
|act_reading_2018|*float*|act_2018.csv|Average score for reading (range between 1 - 36)|
|act_science_2018|*float*|act_2018.csv|Average score for science (range between 1 - 36)|
|act_composite_2018|*float*|act_2018.csv|Average score for science (range between 1 - 36)|

#### Conclusion/Recommendations
Based on the findings, we can draw several conclusions: <br>

1) Exploiting the inverse correlation between SAT and ACT participation rates:
- This correlation is highly influenced by the state policies and entitlements given to the students. Several states that have remained faithful to a specific exam is highly influenced by such factors and therefore it would be a better choice to invest in one that has yet to show such strong preferrence for the ACT exam. One such state would be New Mexico that has a low SAT participation rates and fairly lower ACT participation rates across the 2 years. 

2) Learning from states with higher SAT participation rates:
- Most of these states either provide free SAT tests or do not mandate a particular test. Therefore a state that shares such aspects would be our state of choice. 

One such state would be **New Mexico** that has a low SAT participation rates and fairly lower ACT participation rates across the 2 years. Moreover, universites in New Mexico accept either the SAT or the ACT test the state provides This is promising as that there is a huge room for growth in SAT participation rate with an impressionable market. One recommendation would be to increase the accessibility of SAT exams through several avenues such as adopting a SAT School Day to provide free SAT to students or to make SAT exams free of charge. To implement such a School Day, more data should be collected on dates which are the most popular so as to accomodate a wider range of students. 


---

