# Stock Price Prediction

[View code in colab](https://colab.research.google.com/drive/1IsNvAF3Mpkce_qUnzS2wQ357lufIANdk?usp=sharing)

### Objective

The goal of this project is to create a hybrid model for stock price/performance prediction using a combination of numerical analysis of historical stock prices and sentimental analysis of news headlines.

### Data

For the purposes of this project, I’ll work on analyzing and predicting SENSEX (S&P BSE SENSEX).

For stock prices, I used [yfinance](https://pypi.org/project/yfinance/) library which scrapes data from [yahoo.finance](https://finance.yahoo.com/).

 

![yfinance snippet](https://github.com/azizamari/azizamari.github.io/blob/master/assets/projects/case_study/stock/yfinance.PNG?raw=true)

![Historical Stock Data](https://github.com/azizamari/azizamari.github.io/blob/master/assets/projects/case_study/stock/histdata.png?raw=true)

For the (textual data) news headlines I used [Times of India News Headlines](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/DPQMQH) dataset.

### Sentiment Analysis

I used [NLTK - Natural Language Toolkit](https://www.nltk.org/) to preprocess headlines, perform stemming and remove stop words.

Then used [TextBlob](https://textblob.readthedocs.io/) for sentiment analysis, calculating **Subjectivity and Polarity**, in order to provide insight for our model on how news and media coverage can impact a stock's performance.

-Polarity > 0 means the text is positive otherwise negative

-Subjectivity quantifies how personal or factual it is, high subjectivity means it is more of a personal opinion

![Text blob snippet](https://github.com/azizamari/azizamari.github.io/blob/master/assets/projects/case_study/stock/textblob.png?raw=true)

Then calculated negativity, positivity, neutrality, and compound using nltk’s Sentiment Intensity Analyzer

### Merging Data

First, I merged the stock’s historical data and resulting data from sentiment analysis then I convert the merged data to a supervised format var(t-1) → var(t)

![var(t) data](https://github.com/azizamari/azizamari.github.io/blob/master/assets/projects/case_study/stock/vart.png?raw=true)

### Resulting Hybrid Model - LTSM

After splitting the data to test and train I built and trained a simple LTSM model using [tensorflow](https://www.tensorflow.org/).

![Tensorflow model code snippet](https://github.com/azizamari/azizamari.github.io/blob/master/assets/projects/case_study/stock/model.png?raw=true)

Comparing training and validation loss:

![Loss visualization](https://github.com/azizamari/azizamari.github.io/blob/master/assets/projects/case_study/stock/lossgraph.png?raw=true)

### Inference on Test Data

We achieved a root mean squared error of 111.046 which is good enough considering the magnitude of SENEX price values.
