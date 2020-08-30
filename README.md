# Executive Summary
## Science or Science Fiction?
### Can we spot the difference? 
---
#### Problem Statement

1. Can a predictive model be built to classify a reddit submission into science or science fiction categories with a higher than 70% accuracy?
2. Which model is the best at predicting the class of the content?
3. Which pre-processing methods and estimator parameters prove to work best when predicting the class of the content?

#### Table of Contents

**Code:**
 * [getting_data](getting_data.ipynb)
 * [data_cleaning](data_cleaning.ipynb)
 * [EDA](EDA.ipynb)
 * [modeling](modeling.ipynb)
 * [model_tuning](model_tuning.ipynb)<br>
 
**Data:** 
 * [original_data](reddit_working.csv)
 * [cleaned_data](reddit_working.csv)<br>
 
**Presentation:**
 * [presentation](Presentation.pdf)
 
#### Data

For the purposes of this project two subreddits were selected:

[r/askscience](https://www.reddit.com/r/askscience/comments/g45x1t/is_it_a_myth_or_a_fact_that_dogs_can_sniff_cancer/
) <br> Created: September 5, 2008. <br> Members: 18.9m <br> Description: ask a science question and get a scientific answer. <br>

[r/scifi](https://www.reddit.com/r/scifi/) <br> Created: January 25, 2008. <br> Members: 1.6m <br> Description: science fiction, speculative fiction, fantasy - books, movies, TV. <br> 


From the two subreddits submission title, text, timestamp, permalink and id had been extracted with Pushshift's API. 

Noteworthy, that while askscience has over 18.9 million members, scifi only has 1.6 million. Because of this large difference, webscraping yielded substantially more data-points for askscience than for scifi. <br>

**r/scifi:** 96_635 rows from Jan. 27, 2008 - Apr. 19, 2020
 
**r/askscience:** 805_809 rows from Oct. 13, 2014 - Apr. 18, 2020

|Final Data Frame| Size | Method|
|----------|----|------|
|Scifi|24_351|All|
|Askscience|24_351|Random Sample|
|Combined|48_702|Combined|

---
#### Data Analysis

**Models Tested**<br>
<sup><sub>*(15_630)*<sub><sup>

|Transformers|Estimators|
|------------|----------|
|Count Vectorizer|Logistic Regression|
|TF-IDF Vectorizer|Bernoulli Naive Bayes|
| |Decision Tree Classifier|
|Word Net Lemmatizer|Ada Boost Classifier|
|Porter Stemmer|Gradient Boosting Classifier|

---

### Conclusion

**1. Accuracy of best model:** 
 94.5% (cross validated) > 70%
    
**2. Best model:**
Regularized Logistic Regression with TF-IDF Vectorizer

**3. Parameters of best model:**

|**TF-IDF Vectorizer**| **Regularized Logistic Regression**|
|:---------------------|:-----------------------------------|
|Max_features = 10_000 words |      C = 1.85 |
|Stop words = None |
|Ngrams = 1-grams | |
    
---
#### Recommendations

The final model sorts subreddit posts into their appropriate categories with a 94.5% (cross-validated) accuracy, which is way above the 70% benchmark we set. However, there is room for improvement. Science fiction discussions and theorizing may carry similarities to the speech patterns observed in conspiracy theories and fabricated reality-stories. Should we want to add the findings of this data analysis to the growing body of classification models built to distinguish 'fake news' from real ones, I recommend extending research into two directions:
- remove book/ TV and movie related words from the r/scifi posts - and verify if the difference between science and science fiction related texts still is substantial enough for a machine learning model to differentiate between the two
- compare r/scifi with subreddits identified as 'fake news' to find possible similarities and differences in the wokabulary and speech pattern 

[Presentation](Presentation.pdf)
  
<sup><sub>*Source for markdown formatting:* [BalusC](https://meta.stackexchange.com/questions/53800/markdown-extension-for-really-small-tiny-text/53801)<sub><sup>
