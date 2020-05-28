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
<u>Ground score: </u> refers to the a binary score of "positive" or "negative" experience. <br>
<u> Vader score: </u> refers to the score assigned to the text review. NLTK's ``` SentimentIntensityAnalyzer() ``` tool was used to assign sentiment scores to each of the reviews. Each review has a "compound score", "positive", "negative" and "neutral" score. Please refer to <a href="https://www.nltk.org/api/nltk.sentiment.html">NLTK-Sentiment analysis</a> to read more on the scoring process. 

__________________________________________
## Exploration2 - Frequency Analysis:

