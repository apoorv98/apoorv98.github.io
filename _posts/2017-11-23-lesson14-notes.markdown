---
layout:     post
title:      "Fastai Course Summary: Lesson 14"
date:       2017-11-24 18:00:00
author:     "Apoorv Jagtap"
comment:	true
published:  false
category:	deeplearning
header-img: "images/fastai.png"
---

#Time series
starts with a paper from Children's Hospital Los Angeles using RNN to predict mortality risk

#Kaggle competition involving time series
Rossmann car sales: Jeremy discusses the model used by 3rd ranked competitors (as it is simple and can be extended for other problems). Briefly, it involves one hot encoding the categorical variables which are then embedded. These embeddings are concatenated along with continuous variables and passed through dense layer, which is then passed through another dense layer and finally through sigmoid function for output layer.

DataFrame mapper

*try adding if store was open on sunday to see the change in results

#Taxi data kaggle competition
apart from combining the categorical and continuous variables, the clusters to most common destinations (like hospitals, airport) are added after sigmoid. Sigmoid helps to average the clusters and also enables to pick any place as destination, this is quite unique architecture and worth exploring 
