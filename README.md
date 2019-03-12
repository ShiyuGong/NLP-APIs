# NLP-APIs
Google Cloud Natural Language and Amazon Comprehend API are utilized to do sentiment analysis for Yelp Review dataset.

## Overview 
Sentiment analysis is a subfield of NLP and could be applied systematically to identify, extract, quantify, and study affective states and subjective information. In this project, I would use the following two Cloud resources to did sentiment analysis for Yelp Review dataset.

*	Google Cloud Natural Language API
*	Amazon Comprehend API

## Technique

Firstly, the Yelp review dataset collected from Kaggle contains 10K records of Yelp reviews. Each of them has the stars (1-5) and text review provided by customers. The chart below gives us a first look on how the data spread. We can see that the rating tends to be relatively positive (68% of the ratings > = 4), which may be due to the fact that unhappy customers tend to just leave instead of making efforts to rate. Examples of reviews with low ratings and high ratings are as follows.

<img width="214" alt="table" src="https://user-images.githubusercontent.com/43686840/54180485-064d0600-4459-11e9-935f-739618c99aa1.png">

In the modeling part, I would focus on the reviews whose stars are 1 to see whether the sentiment analysis would provide the same negative results based on the text data.

### *GCP- Natural Language API*
For GCP, sentiment analysis attempts to determine the overall attitude (positive or negative) expressed within the text. Sentiment is represented by numerical score and magnitude values.

Score of the sentiment ranges between -1.0 (negative) and 1.0 (positive) and corresponds to the overall emotional leaning of the text. Magnitude indicates the overall strength of emotion (both positive and negative) within the given text, between 0.0 and +inf. Unlike score, magnitude is not normalized; each expression of emotion within the text (both positive and negative) contributes to the text's magnitude (so longer text blocks may have greater magnitudes).

### *AWS Comprehend*
When it comes to AWS Comprehend, it inspects text and returns an inference of the prevailing sentiment (POSITIVE, NEUTRAL, MIXED, or NEGATIVE).

The results of two sentiment analysis are shown above. Based on the results, in terms of 749 records whose stars equal to 1, 86.9% of records are labelled as negative by GCP and 81.2% by AWS.

## Conclusion
In this project, we practice how to use GCP- Natural Language API and AWS Comprehend API to conduct sentiment analysis for text reviews. The results show that most of the reviews with 1 star are identified as Negative in both analyses.

The differences between GCP and AWS sentiment analysis are as follows:

1.   AWS Comprehend provides an inference of the prevailing sentiment (POSITIVE, NEUTRAL, MIXED, or NEGATIVE) directly. GCP Natural Language analyzeSentiment only provides score of the sentiment ranging between -1.0 (negative) and 1.0 (positive). If we want to get sentiment, we need to set the boundary score of each sentiment manually. In this project, I set reviews whose values are greater than 0 as Positve, equal to 0 as Neutral and less than 0 as Negative.

2.  GCP Natural Language analyzeSentiment provides magnitude which indicates the overall strength of emotion within the given text, between 0.0 and +inf, which differs from how AWS Comprehend represents the strength of emotion.


