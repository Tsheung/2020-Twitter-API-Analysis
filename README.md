# 2020-Twitter-API-Analysis
2020 Democratic Candidate Twitter Data Science Analysis with Python

## Description
Analyzing Top 3 Democratic Candidates' Popularity within Twitter API
The upcoming 2020 presidential election has been a hot topic for Americans for a long time. After Donald Trump had been elected, Democrates have been looking for potential candidates for 2020's election. Currently, there are 15 democratic candidates and the numbers of candidates have been rising. But there are three candidates that have been consistingly growing in popularity and people believe that one of the three may be the Democratic candidate to run against President Trump. The top three Democratic candidates are Joe Biden, Elizabeth Warren and Bernie Sanders. All three have high credibility, high followings but have different campaign viewpoints. For this project, I will analyze the most popular Democratic candidate among the three by examining the number of tweets that mention a certain candidate by state. All three of these candidates have a Twitter account and Twitter is known for its live tweeting. Obtaining data from Twitter's API could potentially help understand Americans choice for the Democratic Candidate. But analyzing the number of tweets about a candidate does not mean that a person follows them but I believe that the person has some sort of interest. If a candidate has high interest, I believe the number of supporters will follow.

## Prerequisites:
Keys must be obtained by registering for the Twitter developers API website: https://developer.twitter.com/

## Install:
Install Twython to collect Twitter Streaming Data and Twitter user information

## Import:
Twython, TwythonStreamer, json, pprint from pprint, Counter from collections, pandas

## Collecting Data:
I wanted to examine the most Tweeted about candidate without a geotag to analyze the basis of who people were Tweeting about. I wanted to continuely obtain Tweets for one to two weeks. But ultimately, the streaming of so much data created a memory problem. I decided to collect the 1000 tweets in the afternoon after Kamala Harris decided to drop out of the race.

I used Twython and TwythonStreamer to create a class which contains two functions to collect 1000 live tweets which tagged either @JoeBiden, @ewarren or @BernieSanders. All three of these Twitter accounts are the Democratic candidates' official accounts. The first function on_success, collects tweets that are in English and prints out the number of tweets collects from 1000. Each of the 1000 tweets are appended into a list. The second function on_error, disconnects the Twitter API when the 1000 tweets have been connected or when an error occurs. After the 1000 are collected, I wrote the list into a json file within the directory.

I then decided that perhaps these 1000 tweets may be different at night when people return home after work. I collected another 1000 tweets by the same parameters as the first collection of 1000 tweets. I separated the second 1000 tweets into another json file. Json files are not good with appending data and it was best to keep it separate.

## Collecting Data by Geotags:
The purpose of this project was to examine the most popular candidate by state so I used the search function within Twython to collect 100 tweets that tag either Joe Biden, Elizabeth Warren or Bernie Sanders. The search function allows the input of a geocode to examine a certain coordinate. I used https://www.latlong.net/category/states-236-14.html to examine the geocodes for each state and decided that a 50 mile radius of that coordinate would be enough to capture a state. I did not want to increase the radius in hopes to not capture those out of that state. The 100 tweets were appended into a list and written into separate json files. In total, there were 5000 tweets from the collection of 100 tweets from each state.

## Analyzing from 1000 Tweets:
I analyzed the 1000 tweets from the afternoon by accessing their files and appended each Tweet's location by whether or not it mentioned @JoeBiden, @ewarren or @BernieSanders into separate lists. If it mentioned more than one candidate, I appended the same Tweet's location into both of lists or all three of the lists depending on the Tweet. The Tweet's location is the user's location information and was more telling of the user's location. But some location are not real and you never know whether or not a user is lying about their information. Nevertheless, I was able to examine the count of how many Tweets mentioned the certain candidate and I used a counter examine the most common locations the users were from for each Democratic candidate.

I repeated the same tactics to the other 1000 Tweets and found similar results in count and that Joe Biden was mentioned more than Elizabeth Warren or Bernie Sanders from the 2000 Tweets.

## First 1000 Tweets: <br>
Joe Biden = 440 <br>
Bernie Sanders = 212 <br>
Elizabeth Warren = 106

## Second 1000 Tweets: <br>
Joe Biden = 465 <br>
Bernie Sanders = 270 <br>
Elizabeth Warren = 134

The counter that contained the most common location were very scattered and but interesting to examine the long list for user that tweeted about Joe Biden.

## Analyzing Tweets by State:
I used pandas to create a dataframe that could create a table of number of tweets for each candidate by state. I create a list that contained the name of each state's file which was the states' abbreviations. I then created a function that opened the file by name and kept count of the number of tweets that mentioned the three candidates. Lastly, the function appended the row of informtion into the pandas dataframe. After appending all 50 states within the dataframe, I reset the index in case of inconsistances. I created a last row named total to take the sums of each candidates' number of tweets from each state.

Examine the dataframe in the other jupyter notebook containing the code to examine by state results. It could be possible to analyze the most popular candidate by state.

## Total: <br>
Joe Biden = 2094 <br>
Bernie Sanders = 3102 <br>
Elizabeth Warren = 1486

## Challenges:
Some of the challenges for this project was that the times of streaming the Twitters were important factors to consider. I could not continuously stream tweet data for a certain period of time due to the memory and capabilities of my computer. The Twitter API has different accesses based on payments. Because I used the most basic access, the locations of the tweets could only be accessed by geotags. Those with enterprise accounts can filter tweets by locations, city names or states. Another challenge was figuring out that json is not good with appending data. It might of limited my method of collecting data and having to separately create json files for each state. I believe that my data might not be enough to make conclusions of which candidate is more popular just yet.

## Future:
The next steps for future data analysis would be to tokenize each tweets to examine whether or not a tweets is in support or opposition of the candidate they are mentioning. Learning more about natural processing languages would be helpful to better understand how to separate and understand the structure of words. Another step could be to stream for a continously amount of time and it would be more telling of how users felt about each of the three candidates. Having more data would be more useful to creating a more concise conclusion.
