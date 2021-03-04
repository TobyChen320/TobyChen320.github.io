---
layout: post
title: Med Cabinent App
subtitle: Which Strain Is Right For You
cover-img: /assets/img/marijuana-panorama-farm-field-green-65019611.jpg
thumbnail-img: /assets//img/Med Cabinet.png
share-img: /assets/img/marijuana-panorama-farm-field-green-65019611.jpg
tags: [Medication, Cannabis]
---

Cannabis has always been interesting to me. Whether it be used recreationally or medically; I believe that the product itself has many benefits.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/michael_jordan_slam_200.jpg">
</p>  

<h2>What I'm Trying to Achieve</h2>

There is an obscene amount of strains out there and each one has different desired effects on people.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/Average%20Net%20Rating.png">
</p>

So what I wanted to do was create an application that returns the top 5 strains that best fits the user's inputs. The best part about this is that you can configure how many predictions you want. Meaning it can recommend any amount of strains best suited for you based on how many different strains you want.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/b6ab65_36cbbba46c204d72ae83192b4d8211a6_mv2.webp">
</p>

As I was the machine learning engineer for this project, it was my responsibility to train a model that is usable for the Web team to utilize.

<h2>Process</h2>

I had to merge 2 different datasets to get both the strain names and their descriptions.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/f0d032ebe20ee4cf652b239a6c07924356ea8168/img/5d50e67c682304179915e09dab6ae0f74c1ba1d8.svg">
</p>

Aftewards I had to tokenize the string from the all_text column in the dataset and apply NLP to it which I then put into a 'lemmas' column. I then had to vectorize the lemmas column so that our model is trained to recognize certain weights associated with certain words. 

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/PDP%20Feature%20of%20True%20Shot%20Percent.png">
</p>  

After I vectorized my lemmas columns, all that was left was fitting that into my Nearest Neighbors model.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/f0d032ebe20ee4cf652b239a6c07924356ea8168/img/5d50e67c682304179915e09dab6ae0f74c1ba1d8.svg">
</p>

<h2>Challenges</h2>

A challenge that I had intially was finding datasets that I was able to use for this project. Although there is a lot of data out there in regards to cannabis. It was difficult to procure a dataset that not only has a substantial amount of strains, but also a description associated with each strain to apply NLP to.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/PDP%20Feature%20of%20True%20Shot%20Percent.png">
</p>  

Another challenge I encountered was finding out what exactly should I keep from the original dataset. Every feature in a dataset contains valuable information unless its a duplicate. I had to put myself in the users shoes here and decide what I would want to know alongside a recommended strain's name.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/2%20Feature%20PDP.png">
</p>  

I also had trouble pickling and using my model. To ensure that our app is up and running by the deadline; I decided for us to go a live training route for our model.

<h2>Final Result</h2>

Our application works great; it is able to return the appropriate strains based on the user's inputs. The only issue would be the amount of time it would take to generate each list of recommendations. The time isn't absurdly long; we are talking maybe 2-3 seconds per generated list. However, having 2-3 seconds spent everytime you want to run the app is something that is not ideal. I hope to resolve this sometime in the near future.

<p align="center">
  <img src="https://raw.githubusercontent.com/TobyChen320/TobyChen320.github.io/master/img/ROC%20Curve.png">
</p>  

[Repository Link](https://github.com/TobyChen320/MedCabinet)

[App Link](https://medcabinent.netlify.app/)
