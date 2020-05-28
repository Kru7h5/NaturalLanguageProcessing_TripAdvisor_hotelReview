# NaturalLanguageProcessing_TripAdvisor_hotelReview
## Goal: 
To extract reviews of patrons left on trip advisor and to automatically identify positive and negative keywords and phrases associated with hotels and to better understand characteristics of data analysis tools, extracting explanatory
review summaries, and human reviewing behavior.
__________________________________________
## Setup: 
Webscrape trip advisor website using a city code. The original repo was forked from https://github.com/aesuli/trip-advisor-crawler<br>
The crawler took:<br>
``` trip-advisor-crawler.py [-h] [-f] [-r MAXRETRIES] [-t TIMEOUT] [-a {Hotel,Restaurant}] [-p PAUSE] [-m MAXREVIEWS] -o OUT ID [ID ...] ```<br>
The CMD command used for this example is: 
``` $python3 trip-advisor-crawler.py -o data ca :154922``` <br>
where the ID was 154922- corresponding to British Columbia. 
__________________________________________
## Exploration1 - Vader score vs ground score:
> Ground score: refers to the a binary score of "positive" or "negative" experience. <br>
> Vader score: refers to the score assigned to the text review. NLTK's ``` SentimentIntensityAnalyzer() ``` tool was used to assign sentiment scores to each of the reviews. Each review has a "compound score", "positive", "negative" and "neutral" score. Please refer to <a href="https://www.nltk.org/api/nltk.sentiment.html">NLTK-Sentiment analysis</a> to read more on the scoring process. 
__________________________________________
## Exploration2 - Frequency Analysis:
Retrieving the top-k words used in a positive review vs the top-k words used in a negative review. Induvidual words without context offered little insight into the reviews or provided any valuable feedback on the performance of the hotels. This was treated as a good starting point for further exploration in phrase analysis and MI(mututal information) and PMI (pointwise mutual information)
__________________________________________
## Exploration3 - Language processing:
A pipeline was constructed so that the raw reviews could be fed into the pipeline and the resulting dataframe would contain reviews with scores attached to the popular identified phrases. A list of the top-k phrases were also retrieved along with the number of occurances for visual inspection. 
> Chunking: <br> A chunking string was used to primarily concentrate on nouns and adjectives. The `RegexpParser` of the NLTK library was used for the chunker to perform POS tagging.  
for more grammatical extraction: <a href="https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html">Part-of-speech tags</a> 
> Stop words: <br> NLTK corpus for stop words was used to identify and remove stop words. Length of words was also taken into account to extract only useful words. 
> Stemming and lemmatization: <br> `nltk.WordNetLemmatizer()` and ` nltk.stem.porter.PorterStemmer()` were used to perform stemming and lemmatization. 
__________________________________________
## Exploration3 - Mutual Information:
The mutual information score for popular phrases were calculated in the `getMI` function using the `metrics.mutual_info_score` function from the `sklearn` library. This information was then used to compare to the PMI (pointwise mutual information) score to understand the difference. 
*insight into results in the given context is provided in notebook.*
__________________________________________
## Exploration4 - Pointwise Mutual Information:
PMI scores calcuate the MI score with the addition parameter of the frequency of occurance of the words/phrases in the text. This causes the scores to be more reasonable since they are normalized as opposed to MI which calculates mututal information without accounting for the occurance. The scores are calculated for all reviews, positive reviews only and negative reviews only. 
__________________________________________
## Findings:


