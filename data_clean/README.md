# DATA CLEANING 
Yelp business reviews are divided into 22 top categories2 with multiple subcategories, since this project will be focusing on just healthcare reviews, we will drop any non-healthcare and medical reviews from our dataset. 

## CLEANING STEPS 
Starting first with the business dataset loaded in padas and selecting seven useful columns and dropping the rest. 

- business_id
- categories
- city
- name
- review_count
- star_avg
- state


Since this project will be focusing on only US Healthcare reviews, any business outside of the US was dropped by filtering on city and state columns and dropping any null values with 2 or more null rows. 
  
To select only healthcare related businesses, the categories column was expanded and filter by only choosing categories that fell under the ‘Health and Medical3 and dropping any business that did not fall under that filter. 
With this new healthcare business dataset groping by categories and counting total reviews, a new categorical column was created by selecting the top healthcare subcategories and labeling each business according to its top category creating nine categories. Most businesses fell under these top categories 

- chiropractors 
- hospitals 
- family practices
- obstetrician • 
- diagnostic service • 
- urgent care • 
- physical therapy • 
- mental health 


Finally, the newly clean business dataset was merged with the review dataset by using pandas merge on business_id, a column that both datasets. 
health 

## DATA CLEANING RESULTS
- Original dataset
    - Total business: 188,593
    - Total Reviews: 5,996,996
- Healthcare only dataset
    - Total Business: 3,062
    - Total Reviews: 44,918 


## Sentiment Values

### Polarity and Subjectivity values

Polarity and subjectivity values were taken for all 44,918 reviews creating two new columns in the dataset with its respective names. 
```python
polarity = lambda x: TextBlob(x).sentiment.polarity 
subjectivity = lambda x: TextBlob(x).sentiment.subjectivity 
# create new cols 
df['polarity'] = df['processed'].apply(polarity) 
df['subjectivity'] = df['processed'].apply(subjectivity) 