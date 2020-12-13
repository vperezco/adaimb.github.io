---
layout: home
title: Predicting the Present 
subtitle: Ok Google
use-site-title: true

---

![](../img/fabrizio-verrecchia-Ai7sV3SSMIQ-unsplash.jpg){: .align-center}

It has been common knowledge for quite some time that **Google**, amongst other companies, have a great influence on events. People were made even more aware of this influence, recently, during the 2016 American elections. 
A group of researchers have recently developed a theory which states that Google Trends allow to predict the present. You must ask yourself, **how can we predict the present ?** The idea is to use Google Trends from previous weeks or months and see if those trends give us a good representation of what is happening right now. 
We decided to use the methods behind this theory to pursue a project of our own. 

First of all, we decided to study the link between initial claims for unemployment benefits and specific google trends. This example was presented in the original paper but we decided to view the data on another type of figure to give us another perspective and to push the analysis further by applying the method on another time scale.   

The  aim  of  the second part of our project was to study how Google Trends allow us to forecast near-term values of economic indicators, the US dollars/euro rate in our case. Google Trends are widely used in economic studies since the principal  advantage  is  that  Google search  data  is  easy  to  acquire  and  provides  economically significant  improvements  in  forecast  performance. The latter is of  particular  interest  to  central  banks  and  other  government agencies.
Some time period are of particularly interest to us, especially the 2007 recession period. Indeed, it is quite obvious that the economic indicators changed radically during this period, but it would be even more interesting to see if Google Trends of weeks/months preceding this period could partly explain the change in those economic indicators. 
To help us on our project, we relied on a paper (reference) which carried a similar project and it allowed us to have an overview of the Google Trends we should look at. 

## Structure:

This page is structured in three sections:

## Index
1. [What are Google Trends](#trends)
    1. [What does Google Trends measure anyway?](#meaning)
    2. [Example: The rise and fall of the blu-ray](#bluray)
2. [A data Story](#story)
    1. [The curse of unemployment](#unemployment)
    2. [Will we ever get a job some day?](#job)
3. [ How do I get the best exchange rate ?](#exchange) 
    1. [Google Trends and the forecasting performance of exchange rate models](#model)
    2. [Can we predict the financial drops ?](#drop)



<a name="trends"></a> 
# 1. What are Google Trends

<a name="meaning"></a> 
## 1.A. What does Google Trends measure anyway?

![Image](../img/Trends.jpg)

<br>
<br>

From the FAQ of Google Trends: 

*Each data point is divided by the total searches of the geography and time range it represents to compare relative popularity. Otherwise, places with the most search volume would always be ranked highest.
The resulting numbers are then scaled on a range of 0 to 100 based on a topic’s proportion to all searches on all topics.* — [Google Trends FAQs](https://support.google.com/trends/answer/4365533?hl=en)

So, it allows us to display interest in a particular topic from around the globe or down to city-level geography. for each word in your search Google finds how much search volume in each region and time period your term had relative to all the searches in that region and time period. It’s **anonymized** (no one is personally identified), **categorized** (determining the topic for a search query) and **aggregated** (grouped together). 

It combines all of queries into a unique measure of popularity and scales their values across the topics so that the **largest measure is set to 100**. Indeed, it does not tell you exactly how many searches occurred for your query but gives a nice approximation.

<a name="bluray"></a> 
## 1.B. The rise and fall of blu-ray

We will take a simple example to illustrate the previous section and show how Google Trends are strongly connected to our present. 

Who remembers blu-rays? This technology was used for a period, but nowadays with the emergence of streaming devices such as Netflix, you will probably make fun of someone asks you to watch a blu-ray with him. With Google trends, we can see the when was the golden age of blu-rays, as that and when it began to collapse. 

![Image](../img/Bluray.jpg)
<br>
<br>

According to Google searches of the term 'Blu-ray Disc' in all countries, we can see that the popularity of blu-ray discs was the highest in 2009/2010, few years after its launch, but decreases continuously since these years because of the emergence of new streaming devices such as Netflix. 

![Image](../img/Bluray-netflix.jpg)
<br>
<br>

It is really cool, isn't it ? 

However, manipulating google Trends could be **tricky**... Indeed, what there are thousand of possible search terms related to a subject, that differs by the formulation, the orthograph etc... So we have to be very careful when it comes to pick a search term to relate it to a phenomenon. Taking the example of the queries related to Employment in France we have the following volume of queries for three different search terms : 

![Image](../img/Google_searches.jpg)
<br>
<br>

We can see that depending on the word, the volume of queries differ A LOT. That is why it is better when it comes to pick google trends to select categories or subjects rather than search terms, because they will group different search terms and we don't risk to pick a search term that has not a lot of queries. 

<a name="story"></a> 
# 2. A data story


Nowadays, we can safely say that job search is one of the main concerns for today's young people. We're not talking about a funny subject here, sorry if it's your concern too, we didn't intend to remind you that you are jobless ^^.  Indeed, the world has entered a new demographic, geopolitical, economic and socio-cultural situation. In this world, employment is an essential element for functioning of industrial societies and of the place of individuals in social relation. 

Even if today the society is well-evolved and most of the people benefits to be in good health, educated and trained to a high standard, a lot still struggle to find an employment and get inserted in the society. In this context, it could be interesting to analyze rates of unemployment initial claims to see how much people are searching a job and relate this to a specific period. But, why the unemployment initial claims are increasing or decreasing? 

To interpret this, it could be interesting to use Google Trends to predict these observations and find out if they are somehow related to a societal elements (like an economic crisis, a pandemic etc...). The second goal is to see the how reliable this model is, if we can rely on these predictions to adapt political and economic decisions.


<a name="curse"></a> 
## 2.A. The curse of unemployment

Can we predict how many people won't have a job tomorrow and will ask for unemployment benefits ? Well, we will try to !

**Forecasting** is a technique that uses historical data as inputs to make informed estimates that are predictive in **determining the direction of future trends**. Businesses utilize forecasting to determine how to allocate their budgets or plan for anticipated expenses for an upcoming period of time. This is typically based on the projected demand for the goods and services offered. Forecasting is often based upon a **specific period** (the passage of the next 12 months) but also on the **occurrence of an event**, which could be reflected by the Google Trends.

We are using here a simple model called *Linear Autoregressive Model* 

Are you lost because you don't know what that is ? Don't worry, we will give some more details. 

This model is like a linear regression, but instead of predicting the response (here the initial claims for unemployment benefits) with other observations that might be related to the response , we will predict our response basing us on previous observations of this same observation. So we have the following relation: 


<div align="center"> y(t) = b1*y(t-1) + b0 +e(t)  </div>
    
where *b1* and *b0* are the coefficients obtained fitting the model. We will call this the base model. We will train this model for the period between 2011 and 2020.

Once we have this model, it's time to play with the Google Trends ! 

We are using here the trends *Local/Jobs* and *Society/Social Services/Welfare & Unemployment* for 2 reasons. The first one, these are categories, that means that they identify all the queries that are related to *Jobs* and *Welfare & Unemployment* so we don't have the problem of not taking the right search term to predict the response. The second is that these categories have been identified to be the most useful for this subject. 

The trends model look like this : 

<div align="center"> y(t) = b1*y(t-1) + b2*Jobs + b3*Welfare & Unemployment +  b0 +e(t) </div> 
    
Now, we will train both models for the period from 2004 to 2011 and predict the initial claims for the same period and we get: 

![Image](../img/Initial-claims2004:2011.jpg)
<br>
<br>

It's crazy how the predictions are close to the true observation, right ? And we can go further and compute the improvement of the trends model, and the result is that Google Trends improve the predictions about **0.53%**. We have not an extraordinary improvement, but it is a good start. Furthermore, we can **optimize** the model in funciton of two parameters: 

- The type of seasonal terms 
- The set to train the model

We are going to predict the overall initial claims by using different seasonal terms and find out what are their impact on the prediction accuracy. We are also going to change the size of the traininig set using a **rolling window**. The principle a rolling window is to use a certain number k of previous observations to train the model predict the next one. 

![Image](../img/seasonal_terms.jpg)
<br>
<br>


![Image](../img/rolling_windows.jpg)
<br>
<br>

We can see for our initial claims data set that the model using the observations from eight months and using a rolling window of size 3 gives us a better prediction and achieve an overall improvement of **83%**. We can conclude from this that manipulate these parameters to assert which one is more appropriate for our dataset is essential and it is specific to the data itself. 

<a name="job"></a> 
## 2.B. Will we ever get a job some day?

We will now show that it is possible to predict the unemployment rate for the next months, in other words we could almost say that we are trying to predict the rate of people who do not have a very great life at the moment. 
So if we train the models for the time period from 2011 to 2020 and we predict for the same period we get :

![Image](../img/iclaims2011-2020.jpg)

<br>
<br>


The first thing that we notice is 2020, this sudden increase in the unemployment initial claims. What happened here ? I mean, during the recession there also was an increase where the log of claims reached 14, but here its reaching almost 17 ! And it is safe to say that this might be due to the pandemic. 
Looking now at the predictions, can see here that the **trends model improves the prediction about 19.54% on the overall period and about 42.96% in 2020**. From this we can conclude that the trends model helps to improve the predictions compared to the base model. 

However, now can the fact of predicting over a period in which we already know the ins and outs be useful? In real life, when we try to forecast, we don't know the response because it's what we are searching ! So now, we are in december 2019, the New Year comes, everybody is asking you what are you plans for 2020, and you know exactly what it is... your plans for 2020 are to predict the unemployment initial claims ! Will Google trends help you to build a solid prediction for 2020 ? That's what we are going to find out !

Our base and trends models is now trained for the observations from 2011 until December 2019, and our prediction period will be from January 2020 to November 2020. 

// GRAPH OF THE PREDICTION HERE

Predicting with an out-of-sample forecast gives an improvement of **28.24%** for the trends model compared to the base model. We can clearly see this improvement in the graph, and we can conclude that the base model didn't foreseen this pick coming ! So that clearly proves that for out-of-sample forecasting, base models are not very reliables... However, even if the trends model is not perfect, it somehow managed to predict this crisis due to the actual pandemic. **Why is that ?**

Looking at the ANOVA tables of both models, we see that the coefficient for the s1 feature is really small compared to the intercept and the trends features, and its p-value is above 0.05 which means that this term is not very significative to predict the response. That's could be why the trends model performs better. 


<a name="exchange"></a> 
# 3. How do I get the best exchange rate ?

<a name="model"></a> 
## 3.A. Google Trends and the forecasting performance of exchange rate models
EXPLAIN THE MODEL (WHAT TRENDS, WHY ONLY ONE SEASONAL TERM ETC...)
TABLE WITH MAES, EXPLANATION
FIGURE 


<a name="drop"></a> 
## 3.B. Let's take a look at the financial drops ?
-2008
-2009 (increase) - 2010 (decrease)
-2013 (increase) - 2014 (decrease)

Can we use the google trends model to predict financial recession?

[//]:#(---------- END OF WHAT IS VISIBLE ----------------)
