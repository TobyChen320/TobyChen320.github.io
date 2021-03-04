---
layout: post
title: What Makes A Good Player
subtitle: Predicting a Minimum Net Rating of 1
cover-img: /assets/img/tj-dragotta-qFIiJNjqB10-unsplash.jpg
thumbnail-img: /assets//img/michael_jordan_slam_200.jpg
share-img: /assets/img/tj-dragotta-qFIiJNjqB10-unsplash.jpg
tags: [Basketball, NBA]
---

I've always enjoyed basketball; both playing it and watching it. There are many players in the NBA, but very few of them ever end up becoming great. Not many people can be like Michael Jordan or Bill Russell.  

<h2>Average Rating</h2>

At the same time, the average player in the NBA cannot be horrible either because they are the cream of the crop in the basketball world. So I took a data set compiled of every player from the past 2 decade along with their stats to figure out how well does the average NBA player perform.  
 
<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/Average%20Net%20Rating.png">
</p>

I took the net rating of all players starting from the 1996-1997 season until 2019-2020 and got an average net rating of -2. A net rating is determined by your offensive rating minus your defensive rating based on the number of possessions(usually out of 100). What this translates to is that the average player in the league would cost them about 2 points.  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/b6ab65_36cbbba46c204d72ae83192b4d8211a6_mv2.webp">
</p>  

I originally wanted to predict which teams are going to make it to playoffs as well as who is more likely going to win the entire series. This however required more data that I can get my hands on. There are just way too many factors at play to predict those. So I decided to focus more on the net rating of players. With a minimum requirement of a net rating of 1 to be considered "Good", I trained a model to predict if a player is going to be good or not. Using Eli5; I narrowed down which features plays how big of a role in determining which players are considered "Good".  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/Eli5.png">
</p> 

"ts_pct" is true shooting percentage which measures a players efficiency at shooting the ball.  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/f264ef06b993fd1e3c1305a0b82098f912152685/assets/img/5d50e67c682304179915e09dab6ae0f74c1ba1d8.svg">
</p>

<h2>Feature Importance</h2>

This was by far the most important feature in my model as it basically evaluates how likely the player is going to convert a possession into a basket.  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/PDP%20Feature%20of%20True%20Shot%20Percent.png">
</p>  

According to my model; as a player's true shooting percentage goes up so does their net rating. I then use the second most important feature in tandem with the true shot percentage to see at the very least the correlation between these two features and the influence they have over a player's net rating.  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/2%20Feature%20PDP.png">
</p>  

Clearly the more games you play the more opportunity you would have in increasing your true shooting percentage. At the same time though; the opposite can happen where you consistently play bad games so your true shooting percentage drops. There are other factors at play as well.  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/Shap.png">
</p>  

<h2>ROC_AUC Score</h2>

I had a ROC_AUC score of .76 which isn't the greatest score to have but at the same time its not terrible. At the very least; it was way better than the .695 I got from the random tree classifier model. It is within an acceptable margin; and my model is very flexible in the sense that it is meant to determine if a player overall is going to have a minimum net rating of 1. With some more fine tuning you can apply this model to draft picks based on stats certain potential prospects have displayed as well as calculating the overall net rating of a team to determine which team has the highest chance of making/winning the playoffs.  

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/assets/img/ROC%20Curve.png">
</p>  

Dataset Link(https://www.kaggle.com/justinas/nba-players-data)