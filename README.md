# Project 3 - Web APIs & NLP

## Problem Statement

We are a group of data scientists working for a young yoga studio (Moga Yoga). The team was tasked to work together with the marketing team to entice more members to subscribe to the studio and maximise ad spend. 

As the pandemic rages on, increased focus on mental well-being has driven a demand for meditation/yoga apps or classes. This would serve as an opportunity for customer base expansion and the need to tailor advertisements to promote yoga as a coping strategy / self-care tool. 

To maximise the effectiveness of our marketing campaigns to yoga enthusiasts, we have examined submissions under 2 subreddits - r/yoga and r/Meditation. These are commonly referred to as 2 different practises even though Meditation **is** an integral part of yoga. By capitalising on their similarity in nature yet differences in mode of practicising, we hope to build an effective NLP classification model to better target yoga enthusiasts. 

The model will help us to
1. identify top predictors for r/yoga to investigate the needs and wants of yoga enthusiasts
2. identify trending words to tailor advertisements for the yoga enthusiasts and also possibly extend the scope to meditation seekers to consider picking up yoga.

## Summary

1500 submissions were scrapped from each subreddit to form the dataset. The dataset was then cleaned by checking for null values, duplicates, and preprocessed for the modelling stage. 

6 classification models were tested (permutaions involving (i) CountVectorizer or TF-IDF Vectorizer and (ii) Logistic Regression, Multinomial Naive Bayes Classification or Random Forests Classification.

The metrics examined included:
- Accuracy (higher score indicting more correct predictions)
- Recall (higher score indicating less false negatives; how many yoga submissions did we misclassify)
- F1 (balance between precision and recall)
- AUC-ROC (how well the model can distinguish between the 2 subreddits)

The model using **CountVectorizer and MultinomialNB Classification** scored the best across the 4 metrics combined.

## Final Recommendations
3 aspects we can focus on for marketing to attract the yoga enthusiasts:
1. Complimentary mat for new subscribers to the studio
2. Aspect of pain and poses
    - services to provide guidance on correct body posture for yoga poses 
    - additional co-instructor would be useful for on-site classes to guide students (not a priority if classes remain small in size)
3. Videos 
    - video-conferencing for online consulting
    - provide recordings of live yoga sessions as a privilege to members only

The common predictors for Meditation and yoga were general and neutral. It would be difficult to work with the current findings to enhance marketing to meditation seekers to look to yoga as a potential self-care tool. 

## Future Enhancements
- Modelling on a larger dataset
    * Scrap data from ***Hot*** and ***Top*** sections of subreddit
    * Investigate ***Comments*** sections on submissions
- Explore different classification models
    * E.g. SVM, Gradient Boosting, etc.
- Update Stop Words
    * To get more meaning keywords to drive marketing policies

## Conclusion
With the current model, we are able to identify useful keywords that gave us insights on potential marketable services and promotions to attract more members to our studio. This would be limited to yoga enthusiasts until further enhancements are done to find keywords which would help target meditation seekers.

## Data Dictionary

| Feature             | Type    | Description                                                                                          |
|---------------------|---------|------------------------------------------------------------------------------------------------------|
| subreddit           | object  | The subreddit the submission belongs to. In this dataset, it would either be r/yoga or r/Meditation. |
| title               | object  | The title of the submission.                                                                         |
| selftext            | object  | The submissions’ selftext.                                                                           |
| is_self             | boolean | Whether or not the submission is a selfpost (i.e. text-only).                                        |
| num_comments        | integer | The number of comments on the submission.                                                            |
| created_utc         | integer | Time the submission was created, represented in Unix Time.                                           |
| created             | object  | Time the submission was created, represented in YYYY-MM-DD HH:MM:SS                                  |
| removed_by_category | object  | Denotes who the submission was removed by.                                                           |
| banned_by           | object  | Denotes who the submission was banned by.                                                            |
| author              | object  | Redditor's alias.                                                                                    |
| url                 | object  | URL of submission.                                                                                   |
| score               | integer | The net upvote count.                                                                                |
| upvote_ratio        | float   | The percentage of upvotes from all votes on the submission.                                          |
| text                | object  | Concatenated 'title' and 'selftext'.                                                                 |
| stopwords           | integer | Number of stopwords in submission.                                                                   |
| punctuation         | integer | Number of punctuation in submission.                                                                 |
| hastags             | integer | Number of hashtags in submission.                                                                    |
| numerics            | integer | Number of numerical characters in submission.                                                        |
| upper               | integer | Number of uppercase words in submission.                                                             |
| title_word_count    | integer | Number of words in 'title'.                                                                          |
| word_count          | integer | Number of words in 'text'.                                                                           |
| char_count          | integer | Number of characters in 'text'.                                                                      |
| avg_word            | float   | Average word length of words in 'text'.                                                              |