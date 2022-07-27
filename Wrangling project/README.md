# Reporting: wrangle_report

## Gathering Data:

My wrangling efforts for the WeRateDogs Twitter project included gathering data from the 
following sources:
- The WeRateDogs Twitter archive. The twitter_archive_enhanced.csv file was provided to Udacity students. This archive contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017.
- The tweet image predictions, i.e., what breed of dog (or another object, animal, etc.) is present in each tweet according to a neural network. This file was provided. 
- Twitter API and Python's Tweepy library to gather each tweet's retweet count and favorite ("like") count at minimum.

## Quality Issues

### 1. Twitter Archive DataFrame

The twitter archive dataframe had 2356 rows and 17 columns. <br>
Several of those columns i deemed unnecessary for data analysis as my of them had no values (NaN) and therefore i used the pandas drop method on axis=1 to drop the columns. These columns were:

<ul>
    <li> in_reply_to_status_id </li>
    <li> in_reply_to_user_id </li>
    <li> retweeted_status_user_id </li>
    <li> retweeted_status_timestamp </li>
    <li> expanded_urls </li>
    <li> source </li>
</ul>
        
The data frame was now left with only seven columns that i saw importand for my analysis. <br>
Some of the data in the ratings denominator were not 10. Using a  for loop i set all denominators to 10 as it should be<br>
Another quality issue was with the ratings_numerator columns. 
<br>
The numerator values are expected to be between 0 and 20. 
Using a for loop to access all the values, any  value above 200 was multiplied by 0.01 and all between 20 and 200 were multiplied by 0.1 <br>

### Image Predictions Datafame

The image predictions table had few qiality issues that i dealt with <br>
The quality isses were: 
<ul>
    <li> Columns names p1,p2,p3 were were decriptive enough </li>
    <li> Duplicated values in the jpg_url column</li>
    <li> Inconsistency in the letter capitalization of dog names </li>
</ul>

For the first issue I used the pandas rename method and set the names to first,second and third_prediction from p1,p2 and p3 respectively. <br>
I firther renames pi,p2 and p3_coef to first, second, and third_confidence respetively <br> 
Using the pandas drop duplicated method i eliminated the duplicated image urls in the jpg_url column <br>
The last issue was the Capitalization which was solved using the str.capitalize method <br>

### Tweet Jason DataFrame

For the Tweet jason Dataframe,  i drop all the columns that i deemed unnecessary for data analysis and renamed the id column to tweet_id <br>
These changes were made possible by the use of pandas rename method and drop method. <br>

The only columns left were:
<ul>
    <li> tweet_id</li>
    <li>retweet_count</li>
    <li>favorite_count</li>
    <li>lang</li>
</ul>


### Tidiness issues
I used a for loop to filter dog stages which were doggo, pupper, floofer and puppo and using the cat method i combined the stages into one column called dog_stages to make it easier to analyse the dataframe <br>
The original uncombined dog stages columns were then droped since they were needed no more <br> 

I then combined all the three data frames to form on master dataset that i caould then analyze and use visualizations on.<br>
I named the dataframe <b>"twitter_archive_master.csv"</b>


