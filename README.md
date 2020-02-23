# Stonks

## Inspiration
We wanted to use natural language processing of social media data, along with stock market data, to make predictions about future stock prices. Stock price is inherently a reflection of public opinion, and since social media also plays a similar role, we wanted to see if we could use one to predict the other.

## What it does
Our algorithm scrapes the relevant subreddit related to a given company, and retrieves historical posts. We also get historical stock price data for the company using an API. We then perform natural language processing steps to vectorize each Reddit post, and average these vectors per day. This process also weighs in the number of upvotes each post received. We used these daily Reddit vectors to predict the opening price of the stock on the next day.

## How we built it
We scraped Reddit posts using the PushShift.io API and retrieved stock price data using the AlphaVantage.co API and the Python requests library. We then preprocessed the financial data using pandas, and vectorized and aggregated the Reddit posts using SpaCy. Once we had this data set, we split training and testing data with scikit-learn, and then tried out several models (decision trees, random forest regressors, XGBoost) to see which one performed best on the data. Eventually, we settled on a Random Forest regressor, and we proceeded to tune the hyperparameters. We performed this analysis on the Tesla stock, as a proof of concept, but all of our code is generalizable to any company by changing a couple variables.

## Challenges we ran into
The PushShift.io API only returned 1000 posts per query, so we had to make requests in batches, filtering the posts by their Unix timestamp. We also struggled for a while to decide how to encode the Reddit post data, since we wanted to lose as little information as possible.

## Accomplishments that we're proud of
- We are proud of how we were able to clean and preprocess all of the language and financial data, since none of us had extensive experience with this before now.
- We are also very proud of how we were able to retrieve Reddit post data in spite of a reluctant API.

## What we learned
This was our first experience working on a full, large-scale data processing project, so we all learned a lot about extensive data preprocessing, as well as feature engineering.

## What's next for Stonks
In the future, we'd like to train a bigger model using social media data for other companies, or from other websites. We would also like to build some sort of application interface around this algorithm, to make it more accessible to the general public. Finally, we would like to streamline the entire process of data collection, preprocessing, and model training into a single script that we could run on a periodical basis.
