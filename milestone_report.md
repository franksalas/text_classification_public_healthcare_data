

# Define The Problem
There is a need for extracting meaning and learning from external text data relating to healthcare. 
 
# Identify your Client
Healthcare providers


# Describe your dataset
 Yelp Open Dataset, (https://www.yelp.com/dataset) It contains 5.9 million reviews from 188 thousand businesses including healthcare providers. 
## How you clean it/wrangle it?
Two files from the Yelp dataset were used.
- `yelp_academic_dataset_business.json`: it contains business data including location data, attributes, and categories.

- `yelp_academic_dataset_review.json`: it contains full review text data including the user_id that wrote the review and the business_id the review is written for.


First, any healthcare related businesses were extracted from the business dataset, and all but four columns were selected:
- `business_id`: unique id
- `categories`: list of related categories
- `name`: name of a business
- `state`: the state where the business is located.

Since I only wanted businesses from the US, I removed any non-US business based on the `state` column.

Second, the review dataset and all but four columns were selected.

- `business_id`: unique id
- `stars`: value 1 - 5
- `text`: review of business
- `user_id`: unique user id

Third, both filter datasets were join using `business_id` as a key to creating a new dataset with join columns:
- `business_id`
- `categories`
- `name`
- `state`
- `stars`
- `text`
- `user_id`
- 
## Text Pre- Processing and normalization
Column `text` containing review was cleaned using several steps:

- removing accented characters
- expanding contractions
- removing special characters
- stemming and lemmatization
- removing stop words
-  creating new column called`clean_text.`


# List other potential datasets you could use

Previous yelp datasets could be used and web scrapping yelp to include states not included in the original dataset.

# Explain your initial findings
## clean dataset values
- 64006 reviews
- 50427 unique users
-  4572 unique healthcare businesses id
-  3882 unique business names

### Results based on Star review.

| Stars | Total Reviews | Mean sentiment value |
| :--------: | :-------- |:-------- |
|5 | 31726| 0.3039403524457926     |
|4 |4245 |0.2246361878536401 |
|3 |2286 |0.1193112649029954 |
|2 |3761 |0.0419480287655719 |
|1 |21988|- 0.049371961979295505 |





### Results based on States



| State| total reviews | mean star value |mean sentiment value|
| :--------:| :-------- |:--------|:---|
| AZ     | 33923     | 3.348053     |0.16096619253723513
| NV |25565  |3.2711519655779386|0.14903179365400793| 
|NC  |2203  |3.268724466636405|0.15258974664628228|
|OH  |918  |3.1938997821350763|0.1378159373622254|
|PA  |837  |3.3428912783751494|0.14243878395210563| 
|WI  |336  |3.357142857142857|0.1715747625383758|
|IL  |113  |2.7610619469026547|0.08141613020437011|
|SC  | 97 |3.443298969072165|0.20211140557185742| 
|CA  | 11 |5.0|0.1285653535217281|
|OR  |3 |5.0|0.3666666666666667|


## Sentiment Analysis


Sentiment analysis was performed on the text review. The sentiment value ranges from -1 to 1 where values <0 were considered negative, and values > 1 were considered positive. Any sentiment value with 0 was considered neutral.

### Results

Reviews were selected whose star value were 1, and 5 and sentiment values were given based on the original review text and clean version.

|  value |reviews|sent_score|sent_score_clean|   
|------------|-----|---|---|---|
|positive (5)|31726|40940|39717 |   
|negative (1)|21988|12205|13239 |   
|neutral     |0    |569  |758   | 
