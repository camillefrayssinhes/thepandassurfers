---
layout: home
---
<a href="https://en.wikipedia.org/wiki/Apple_Inc.">Apple</a> has been a market leader in the world of technology ever since the launch of its first product. Furthermore, media are more and more being used to study their impact on stock market movements. We aim to show that the rises and falls in stock prices of Apple correlate to the extent that people are talking about Apple, the way they are talking about the company in the media, and the fame of the speakers.

In the following, we want to investigate the reciprocal relationships between the fluctuations of the Apple stock market and media coverage related to this company. We explore the Quotebank data set and filter out any quotes that are not related to the company, the products or its direction board. We then combine it with informations on Apple stock market, collected with the Yahoo Finance API.

What is the role of the media coverage in explaining stock market fluctuations? Firstly, we will ask what is the influence of the people's opinions about Apple expressed in the media on the stock market? Then, we will examine who are the individuals who have influence over potential customers. Do these influencers have an impact on the company image and eventually, on the stock market? The aim is to obtain insights on the interplay between the media coverage and the Apple stock market fluctuations.

### Why Apple?
{% include world_map_apple_stores.html %}

Apple is an American multinational technology company that specializes in consumer electronics, computer software and online services. Apple is the largest information technology company by revenue (totaling $274.5 billion in 2020) and, since January 2021, the world's most valuable company. It is one of the Big Five American information technology companies, alongside Amazon, Google, Facebook, and Microsoft. Today, it is widely spread all over the world, and Apple possesses stores around the world as can be seen below. If you zoom in you might even find the original Apple store at Tysons Corner in McLean, Virginia, USA! 


### Where Are We Heading?

In order to provide the reader with a rough outline, we begin the story with a <a href='#PreCurs'>precursory look</a> into the data we have collected.
This is accompanied by a look at the question <a href='#coverage'>"How does the media coverage of Apple evolve over time and how does it influence the Apple stock?"</a>.
Following the initial overview, we develop our understanding of the data by analyzing the correlation between the stock market movements and the <a href='#sentiments'>sentiments expressed</a> in the quotes.
Then we will go deeper by <a href='#fame'>giving a weight to the speakers</a> according to the Wikipedia page view statistics per year. This allows us to classify them as having a significant influence or a low influence over potential customers.


### Why Is This Important? 

Accurately predicting the stock markets is a complex task as there are millions of events and pre-conditions for a particular stock to move in a particular direction. 
Like most other industries, the financial industry communicates by sharing information and data through the media. People speaking in the media express their emotions and opinions. They also consume media, and in the process are influenced by the sentiments, feelings, and opinions expressed by others. Scientific studies show that people are often influenced by the data they consume, and that their decisions or actions are partly aligned with it. 
Hence, **what if the media would have an impact on the stock market?** For instance, what if a rise in the number of pessimistic words in the market column of a journal would foreshadow a market downturn the next day? 


<a id='PreCurs'></a>

### What the Data Says?

We start with some precursory data visualization to provide a feeling for the data we are working with and to present some first insights.

The original <a href="https://zenodo.org/record/4277311#.YbxD5Swo9pQ"> Quotebank data set </a> consists of 178 million speaker-attributed quotations that were extracted from 196 million English news articles crawled from over 377 thousand web domains between August 2008 and April 2020. This extensive data set does not enable us to directly investigate the reciprocal relationships between the fluctuations of the Apple stock market and media coverage related to this company. Instead, in order to have a great preview of **Apple mentions in the media**, we filter out any quotes that are not related to the company, the products or its direction board. We will then analyse to what extent Apple is mentioned according to time in the media, the influence of the sentiments expressed in the quotes and the impact of the notoriety of the speakers talking about this company on the stock market. 

### How does the media coverage of Apple evolve over time?

Thousands of events occur around the world every day, and humans notice only a small subset of these events. Yet, the media attract attention to specific events. In this regard, **a company’s media visibility will definitely affect its stock price.** Are there any specific patterns we can observe across the years, for instance bigger media coverage when there is the keynote? 

We have a look at the daily number of quotes related to Apple between 2008 and 2020. We highlight in red the yearly top 2% of days with the most quotes. We can already make a few interesting observations. Indeed, we can observe some patterns, that will be further dissected in the next sections. For example we observe a yearly spike in September when the new iPhone is released, or in June with the yearly developer conference. Most importantly **the highest spike the 6th October 2011 is related to Steve Jobs death**, which was widely covered in the media. 

<a id='quotesplot'></a>

{% include daily_quotes.html %}
 
The finance data we process is provided by the <a href="https://www.yahoofinanceapi.com/"> Yahoo Finance API </a> and allows us to recover informations about the Apple stock market since 2008. This API provides quick and easy access to finance metrics for any stock or index. Among the many financial metrics available we decided to focus on the daily stock price and volume. The former will be an indicator of the long term health of the stock, and the latter an indicator of the daily volatility it may experience.

We study the liquidity traded for the Apple stock (*$AAPL*) between 2008 and 2020. Market liquidity depends on how much interest the public has in the particular asset in question. For example, Apple’s stock is much more liquid than the average tech company’s shares. The reason is that the business is well-known, with solid fundamentals, so investors often have a greater interest in it. In the graph below, the liquidity traded is displayed in blue (regular), and the top 2% of days per year for which the liquidity traded is maximal is displayed in red (volatile). We observe the same trend for the top 2% of days for maximal liquidity traded over the years. It seems that **4 to 6 times a year, a higher liquidity is traded and this is likely to correspond to characteristic Apple events** in which the company announces release and information on each new product before it hits the market. This allows the consumer to build a demand for the product before it ever hits the shelf. 

{% include liquidity.html %}

We then study the daily stock price for the Apple stock between 2008 and 2020. The stock price is steadily increasing since 2008. However, we notice some drops, particularly in January 2019. We will try to provide interesting explanations for these drops using the media coverage of Apple in later analyses. Most importantly, we observe a significant drop of the stock price in March 2020. This corresponds to the famous Apple stock 4 to 1 split that has likely been done by the company because high share price could deter new investors. However, the shareholders continued to own the same proportion of Apple stock, since the company had effectively increased at the same time the number of shares in circulation. 

{% include stock_price.html %}

<a id='coverage'></a>

### What Can We Learn From the Data? 

A question sprang to our attention during the analysis of the above plots. Is the stock price correlated to the quotations related to Apple? Let's investigate the **relationship between the fluctuations of the stock market of Apple and the media coverage related to this company** for a period of 13 years (2008–2020). Combining the former observations, we can look into the evolution of the Apple stock price in a joint relation of the number of quotations related to Apple in the media. At first sight, it is not straightforward to accurately determine a correlation between both. 

{% include daily_quotes_related_Apple_stock.html %}

We can conjoin this information with further analyses regarding the qualitative correlation between the number of daily quotations related to Apple and the daily liquidity traded for the Apple stock. We apply <a href="https://en.wikipedia.org/wiki/Pearson_correlation_coefficient">Pearson correlation </a> to identify if the correlation is statistically significant. The <b>Pearson correlation coefficient is approximately 0.3</b> and the p-value is very small (p < 0.05). Hence, there is a non-negligible positive correlation, which indicates that **an increase in liquidity will be likely associated with an increase in discussion related to Apple** and the other way around. In order to go deeper, we can divide the quotations into different categories according to the sentiments expressed (e.g. positive, negative or neutral). We would expect to see a stronger correlation coefficient between the daily liquidity traded for the Apple stock with the number of daily positive quotations related to Apple rather than with the number of daily negative quotations related to Apple. 


From the above observations, we had the intuition that each quarter report released by Apple was synonymous with a day of high volatility. A quarterly report is a summary or collection of unaudited financial statements, such as  gross revenue, net profit, operational expenses, and cash flow. As we have 252 trading days in a year and 4 quarter reports per year, we expect a periodicity of high liquidity days of around 64 days. This in fact validated by the next analysis, which performs a seasonal analysis over a wide range of days period, and keep the periods with the lowest null p-value (i.e the most likely period). Incredibly, **the period that was retained by the model corresponds exactly to the 64 days that separate two quarters!** 

{% include seasonal_analysis.html %}

<a id='sentiments'></a>

## Can We Go Deeper?

## What is the influence of the public opinions or emotions about Apple expressed in the media on the stock market ?


Media influences beliefs by providing compelling information about events. In this regard, the media have been identified to play a significant role in shaping the consensus market opinion. Can a series of news articles make a stock rise? On the other hand, can it send a market into turmoil? We hypothesize that emotions of the public in the media about a company would reflect in its stock price. Indeed, positive news about Apple would encourage people to invest in the stocks of the company. On the other hand, increases in expressions of anxiety, worry and fear would predict downward pressure on the stocks of the company. 

Understanding the author's opinion from a piece of text is the objective of sentiment analysis. Here, **we classify quotes as positive, negative and neutral based on the sentiment present**. We want to answer the following questions : are the stock price drops/rises correlated with negative/positive quotes?

Below, we display the distribution of the quotations from 2008 to 2020 according to their valence. 

{% include all_quotes_sentiment.html %}

For example, the **positive quotes** include: *"This team is unbelievable in creating hardware and software and services and getting them all to work together"* by <a href="https://en.wikipedia.org/wiki/Tim_Cook">Tim Cook </a> - the CEO of Apple -  or *"One reason I'm bullish on Apple is because Tim [ Cook ] is a very capable CEO. And he's one of the few people on the planet who I think is going to excel in an environment that has so many different business lines"* by <a href="https://en.wikipedia.org/wiki/Jon_Porter"> Jon Porter </a>, an American politician. 
The **negative quotes** include: *"What we found out during this investigation is Apple was losing tens of millions of dollars on this and people think oh Apple is a big company, they can handle it, well all those costs get passed on to the consumers"* by <a href="https://en.wikipedia.org/wiki/Michael_K._Williams"> Michael Williams </a> - an American actor - or *"How could Apple be so stupid to conceive of such a flop!"* by an <u>anonymous</u> speaker. 

We can already observe in the above histograms that there are far more positive quotes related to Apple than negative or neutral quotes. How do these histograms correlate with the stock market? 

Below we look at the evolution of the Apple stock price in a joint relation of the number of positive, respectively negative, quotations related to Apple in the media. 

{% include neg_pos_market.html %}

Again, we have a look at the statistical correlation between the number of **positive quotations** related to Apple and the liquidity traded for the Apple stock. We use the Pearson correlation to see if the correlation is significant. The <b>Pearson correlation coefficient is approximately 0.21</b> and the p-value is very small (p < 0.05). We do the same analysis with the **negative quotations** related to Apple. As expected, <b>the Pearson correlation coefficient is only 0.16</b>, thus it is lower than the one for positive correlations, and the p-value is also very small. 

Interestingly enough, both correlation coefficients are positive! Hence, we may say that regardless of the sentiment, **an increase in the number of quotations is most likely associated with an increase in liquidity and volatility of the Apple stock.** Most importantly we observe that positive quotes have a greater correlation than negative quotes. One hypothesis that we may establish is that while negative quotes may make it more likely to sell a higher volume of stocks than usual (e.g. to get rid of the shares), positive quotes have a higher influence on the volatility and the market may be more willing to buy more stocks.

In the next section, let's add another level of complexity in our model by taking into account the fame of the speakers. 


<a id='fame'></a>

## Who are the individuals who have influence over potential customers, and do these influencers have an impact on the Apple company image and eventually, on the stock market?


In the precedent section, we have looked at the influence of the author’s opinion from the different quotes of our data set on the stock market. But yet, we still miss an important piece of information. Indeed, if the previous president of the United States Donald Trump shares his opinion about Apple and if a random postman shares his opinion, it won't likely have the same effect. Thus, what is the impact of the speaker on the stock market? The response is relatively simple, it depends on **how well known the speaker was at the time he or she was quoted in the media.** And a quite simple way to have that indicators is the number of pageviews on then speakers' Wikipedia page (if there is one!).

The reason why we look at the fame of the speaker is that **personality plays a huge role in consumer buying behavior**. Indeed, the high level of public attention and the positive emotional responses that define celebrity increase the economic opportunities available to a firm. We hypothesize that quotes from celebrities significantly impact the stock market, whereas quotes from ordinary people have no significant predictive power. One defining characteristic of a celebrity is that it is a social actor who attracts large-scale public attention : the greater the number of people who know and pay attention to the actor, the greater the extent and value of that celebrity.

Therefore, we speculate that not only the sentiment expressed in the quote, but also the fame of the speaker has an influence on the Apple stock market. 

As an important next step to explore the impact of the speaker fame on the stock market in combination to the valence of the quotations, we need to find a metric to identify how much a speaker is notorious. Are the different speakers poorly influential, moderately influential or highly influential? To achieve this, we use Wikipedia that has almost one page for every famous person. We hypothesize that **the higher the Wikipedia page view statistics, the more notoriety the speaker has**. Considering that we have only access to the Wikipedia page views since 2015, for this part we focus our analysis on the quotations released between 2015 and 2020. 

In the following plot, we have chosen 6 events which were highly mediatized between 2015 and 2020. We chose 6 major events picked up from the 2% in <a href='#quotesplot'>this plot</a> for which we were able to find relevant thematic associated e.g. the "FBI-Apple encryption dispute", "Release of the iPhone X", etc. Quotations were plotted according to their valence and to the fame of their speaker. 

{% include distribution_valence_fame.html %}

<br>


### What is the impact of the quotations according to the speaker's notoriety on the stock market? 

Next, we give a **fame score** to the speakers based on their Wikipedia page view statistics. How to compute this fame score? We begin by normalizing the number of the speaker's Wikipedia page views at the year where the quote was published between 0 and 1. Then we multiply this number by +1 for positive quotes, -1 for negative quotes (and 0 for neutral quotes). Now, we have a fame score for each single quote. Let's try to see what is the impact of this fame score on the stock market? 

In the following plot, we add all the positive and negative scores separately, and we plot them respectively with the stock price. The idea is to identify the days for which a lot of famous people have talked about Apple positively or negatively. Indeed, if poorly influential people have talked about Apple, their score will be low and won't contribute a lot to the total score!

The significant peak at the beginning of 2016 corresponds to the FBI story. What happened at this date? Apple has become embroiled in a very <a href="https://www.nasdaq.com/articles/will-apple-inc.-aapl-stock-feel-a-bite-from-the-fbi-2016-02-23"> public battle with the FBI </a> over whether or not the tech firm should unlock an iPhone used by one of the shooters in the San Bernardino terror attacks. The media had a field day! This debate could have gone either way for the Apple stock. On the one hand, the media could have highlighted Apple's refusal to design a program to unlock iPhones underscores the company's hardline against violating customer privacy, and this likely gave customers another reason to choose Apple products. On the other hand, the media could have shifted the narrative and painted Apple in a negative light for obstructing an investigation into a terror plot, and this could have severely affected the Apple stock.

The plot does not give us a lot of information about the correlation between the fame score and the stock market. We performed a statistical analysis, but unfortunately, the Pearson correlation coefficient between the positive - respectively negative - fame score and the daily stock market liquidity is 0.02 - respectively 0.03 - with a non significant p-value at the level 0.05. A possible reason for these low correlation coefficients is that the fame score we used might not be an optimal metric to estimate the fame of the speakers. 


{% include stock_price_against_quotes_score.html %}

Now that we have done all the basic analyses, can we train a machine learning model to predict the stock market fluctuations by combining all the above informations?

<a id='model'></a>

## How rich would you get if you developed a way to accurately predict the stock market?

### The holy grail of day traders… building a model for stock market prediction

After the basic analysis, we attempt to train a machine learning model to predict the daily stock price using the quotes related to Apple, speakers data and past stock performance. The model is a modular linear regression model, that can take into account past performance and additional factors. The model is trained on data from 2015 to 2017 and predict the daily stock price in 2018.
The resulting regression model did not perform well to predict the stock price during the first semester of 2018. However, it is quite effective in predicting the stock price during the last semester of 2018. Especially, it has well predicted the little drop in the stock price in June 2018! 

{% include future_stock_prediction.html %}

### … but is this that simple?

So far, we have been able to demonstrate that taking into account the media coverage, the sentiments expressed in the quotes, and the notoriety of the speakers, there exists a positive correlation between the stock market and the daily number of quotes related to Apple. Nevertheless, if one looks at the big picture, the correlations are not significantly high enough, and we won't be able with our model to accurately predict the stock market. Unfortunately it's not this way that we will get rich! 

To end this data story, the Panda Riders wish you a Happy Christmas Holidays and a Happy New Year 2022! 
And don't forget that "An AAPL a day keeps the pandas away!" 




