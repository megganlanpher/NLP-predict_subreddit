# Reddit & NLP
___


## Problem Statement

r/AskEconomics and r/askeconomists are subreddits of similar topics, which are, respectively, 
1. “Ask questions of academic economists, so we can all know a little more about one of the most important forces in the human world, and be more educated citizens.”
2. “A central repository for questions about economic theory, research, and policy. Please read the rules before posting.”

Given the title and text submission, I would like to predict if it was posted to the subreddit r/AskEconomics or the subreddit r/askeconomists in order to determine what features may differ among the consumers of each subreddit. 


## Exploratory Data Analysis 

After pulling data from the Reddit API for the given subreddits over the last 7 years, I evaluated the features of the resulting dataset. It appeared that the content of the submissions was contained in the selftext and title features. I also discovered that some documents did not contain text or were instead labeled as 'deleted' or 'removed'. I dropped the columns with these filler values and added a parameter ('is_self' : True) for grabbing the data that seemed to clean much of the missing data, as well as media-based postings. 


## Modeling the Data

In order to feed the models, I created a combined X variable with all of the words from 'selftext' and 'title', then dummied the y-variable of the subreddit each post was listed on. Additionally, I created a customized list of stopwords that included the most popular terms for both of the subreddits. 

I used logistic regression and the multinomial Naive Bayes classifier to model the data, and I evaluated the results based on the accuracy scores from a Gridsearch across the train-test split. The best performing training model was the CountVectorized Logistic Regression; however it had high variance, so the TfidfVectorized Logistic Regression had the best testing scores. 



## Conclusions

In conclusion, I found that the two subreddits had quite similar content/writing. But it seems that there is some evidence of differences between the content. In the end, I was able to predict which subreddit a post would be on with 62 percent accuracy on new data

Furthermore, the AskEconomy subreddit seems to display a larger variety of questions and writing that encompasses just general questions that may relate to the economy (i.e. "help", "product", "supply", "industry"). In contrast, the askeconomists subreddit analysis so far suggests that the questions posed on that site are more niche (i.e. "modern", "return", "situation"). From this analysis, it seems that the AskEconomy subreddit appeals more to consumers of the general public while the askeconomists subreddit may be more relevant to people interested in or currently studying the field.
