---
layout: post
title: City Spire App
subtitle: A city metrics collation app to help find the perfect city
cover-img: /assets/img/171109_08_11_37_5DS_0545__1_.0.jpg
thumbnail-img: /assets/img/1_c65oQ0sAVGHjFpKrrsbiJQ.png
share-img: /assets/img/171109_08_11_37_5DS_0545__1_.0.jpg
tags: [Moving, Cities]
---

For this project my team and I had to make an app that returns certain city’s metrics back to the user as requested by our shareholders. The metrics should include population size, crime rate, forecasted rental rates, walkability score, and a livability score. The purpose of this app is to create a one-stop resource for users to receive the most accurate city information.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/download.jpg">
</p>  

<h2>Process</h2>

We had to scour the internet to find datasets that we can use for each metric being requested. Once that is done; we began cleaning our datasets which took quite a bit of time since some of these datasets are all over the place. We also had to make sure we can deploy our app on AWS Elastic Beanstalk because even if we completed everything else; if our API is not deployed then our Web team can’t access our information which means the user won’t be getting any kind of information from our app at all. 

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/Process-1200x627.png">
</p>

<h2>Challenges</h2>

Our biggest challenge had to be getting our app deployed on AWS Beanstalk. This was the first time for anyone within my team deploying to AWS Beanstalk. We had a bunch of technical issues that took about 2.5 weeks to resolve. We ended up creating a brand new repository from scratch just so we are able to deploy without any issues. The next issue we had was utilizing our model for our rental projections. I used the Prophet model from the FBProphet library which is not pip friendly at all. This led to everyone else not being able to utilize the model because it would require them to install the library packages via Conda as opposed to pip install. We agreed on using Pipenv beforehand because everyone was more familiar with it and it can be easily replicated on anyone’s local machine. The fact that only I can use the Prophet model since I was the only one that Conda installed the packages; I had to create a stop gap which meant I had the model generate the predictions beforehand and saved in a CSV file so all we needed to do was create a method to pull the data.

Stop gap function:
```
from fbprophet import Prophet
for x in range(2263):
    df1 = rent3.loc[rent3['index'] == x][['ds', 'yhat']]
    df2 = rent3.loc[rent3['index'] == x][['RegionID', 'RegionName', 'SizeRank', 'MsaName']]
    df1.columns = ['ds','y']
    df1['ds'] = pd.to_datetime(df1['ds'])
    m = Prophet(interval_width=.95)
    m.fit(df1)
    future = m.make_future_dataframe(freq='MS', periods=12)
    forecast = m.predict(future)
    predictions = forecast[['ds', 'yhat']]
    predictions['yhat'] = predictions.yhat.round()
    predictions['RegionID'] = df2['RegionID'].iloc[0]
    predictions['RegionName'] = df2['RegionName'].iloc[0]
    predictions['SizeRank'] = df2['SizeRank'].iloc[0]
    predictions['MsaName'] = df2['MsaName'].iloc[0]
    predictions = predictions[['RegionID', 'RegionName', 'SizeRank', 'MsaName', 'ds', 'yhat']]
    predictions.to_csv('zip_predictions.csv', mode='a', index=False)
```

At the end of the day though we were able to get our app up and running through many trials and tribulation. It was huge bummer for everyone on the team that it took so long for both the Web team and the IOS team to receive the Data Science endpoints. We had all our endpoints created practically within the first week that we were given this project. The issue was the deployment which caused everything to be delayed. Even if we had endpoints from the beginning, it can’t be utilized without having our app deployed. Our app is currently completely functional but it isn’t as pretty as we would like it to be simply because we didn’t have enough time. The IOS also didn’t have time to hook up their application with our endpoints because they received it so late. Everyone had a great time with this project and the experience that I gained from this in regards to working in a cross functional team is something that I will forever cherish.

 <p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/we-did-it.jpg">
</p>

[Repository Link](https://github.com/TobyChen320/cityspire-b-ds)
