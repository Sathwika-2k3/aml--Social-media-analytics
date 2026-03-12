# AML-3203 — Assignment 2
# Business Question & Success Metric

Business Question:
We want to understand what topics and sentiments appear in US airline tweets and find a way to quickly locate tweets that are similar. This helps airlines respond faster to complaints and highlight positive feedback.


Success Metric:

1. Identify main themes in tweets using topic modeling.
2. Correctly label tweets as positive, negative, or neutral.
3. Return the top 10 most similar tweets for any query accurately.

# Methods (Detailed)
**Data Preprocessing**

Started by cleaning the raw tweets to make them easier for analysis.

Steps we performed in code:

* Converted all tweets to lowercase so words like “Flight” and “flight” are treated the same.
* Removed URLs using regular expressions because links do not add value for sentiment or topic analysis
* Removed punctuation and non-alphabetic characters using regular expressions.
* Split the text into words and removed common English stopwords such as “the”, “is”, and “and”.
* After cleaning, we joined the words back into a single string and stored them in a new column called clean_text.
* This column was used in topic modeling and the recommender system.

**Topic Modeling**

* Used Latent Dirichlet Allocation (LDA) from the gensim library to discover themes in tweets.

How it worked in code:

* Converted the cleaned tweets into a bag-of-words format using gensim.corpora.Dictionary.
* Created a document-term matrix (corpus) for all tweets.
* Ran the LDA model with 5 topics, letting the model find clusters of words that commonly appear together.
* This allowed us to uncover major topics, such as flight delays, cancellations, customer service issues, and positive feedback.

**Sentiment Analysis**

* Used Google AI Studio LLM to classify each tweet as Positive, Negative, or Neutral.

Steps in code:

* Sent each tweet to the LLM API as a query, asking it to classify the sentiment.
* Retrieved the LLM’s response and stored it in a new column called airline_sentiment.
* This gave us a clear idea of how customers felt and allowed us to combine sentiment with topic information.


**Knowledge-Based Recommender** 

Built a simple recommender system to find tweets similar to any query.

Steps in code:

* Vectorized all cleaned tweets using TF-IDF, which converts words into numeric vectors based on their importance in the dataset.
* Calculated cosine similarity between all tweet vectors.
* Created a function recommend_similar_tweets() that:
* Cleans a query tweet in the same way as preprocessing.
* Converts the query into a TF-IDF vector.
* Computes similarity scores between the query and all dataset tweets.
* Returns the top 10 most similar tweets along with their sentiment.
* This system helps identify clusters of complaints or praise for quick analysis.


# Results

**Topic Modeling Results**

* LDA identified 5 main topics from the cleaned tweets.
* Key themes included flight delays, cancellations, customer service complaints, boarding issues, and positive experiences.

Example words showing topics: “flight”, “delayed”, “help”, “cancelled”, “thanks”, “jetblue”, “usairways”, “southwestair”.

**Sentiment Analysis Results**

* Each tweet was classified as positive, negative, or neutral using Google AI Studio LLM.

* Positive tweets highlighted good experiences, negative tweets captured complaints (like delays or poor service), and neutral tweets were general or informational statements.

Example results:

"@SouthwestAir you're my early frontrunner for best airline!" → Positive

"@USAirways how is it that my flight was cancelled?" → Negative

"@JetBlue do they have to depart from Washington, D.C.?" → Neutral

**Recommender System Results**

* Using TF-IDF and cosine similarity, the system returned the top 10 most similar tweets for a given query.

Example query: "@JetBlue my flight was delayed and customer service was unhelpful"

Top returned tweets were related complaints, all correctly labeled as negative.
This shows the recommender can quickly group similar complaints for review.

# Recommendations

* Prioritize negative tweets first for faster response, especially for complaints about delays, cancellations, or customer service issues.
* Use the recommender system to identify clusters of similar tweets, helping customer service address repeated complaints efficiently.
* Validate improvements with an A/B test:

Group A: Handle tweets manually without the recommender.

Group B: Use the recommender to find similar tweets and prioritize.

# Limitations & Ethics

# Limitations:

* Dataset only contains Twitter data, which may not represent all customer feedback.
* Topic modeling may group overlapping themes or mix related issues.
* Sentiment analysis may misinterpret sarcasm or subtle expressions in tweets.
* Recommender performance depends on text similarity and may not capture context beyond keywords.

# Ethical Considerations:

* Tweets are public, but any personal information (usernames, locations) should not be exposed in reports.
* Automated replies should not mislead users; the recommender is meant for analysis, not for posting replies directly.

# References

* Python Libraries Used: 

   pandas, numpy → Data handling
   scikit-learn → TF-IDF vectorization, cosine similarity
   gensim → LDA topic modeling

Dataset: Twitter US Airline Sentiment – Kaggle

Sentiment Analysis: Google AI Studio LLM