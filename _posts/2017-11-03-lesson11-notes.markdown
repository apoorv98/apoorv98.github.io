---
layout:     post
title:      "Fastai Course Summary: Lesson 11"
date:       2016-06-16 18:00:00
author:     "Apoorv Jagtap"
comment:	true
published:  false
category:	deeplearning
header-img: "images/fastai.png"
---

# Introduction

# Related paper reading

# Data Science Bowl Competition
* The approach for solving this problem clearing has to be done in steps, with first step identifing the blobs and zooming in since the images are too big to use neural network directly. This approach was previously used in fish detection system but is more relevant here (and possibly the only choice). The second step would involve detecting nodules for malignant tumor or false positive as the case may be.

The dataset provided on Kaggle unfortunately doesnot provide information for location of nodules which makes it harder to test our nodule detection algorithm for accuracy. On the bright side, there was a previous competition [Lung Nodule Analysis](https://luna16.grand-challenge.org/) which provides the exact information needed in the dataset. So as Jeremy suggest use this dataset first to test our nodule detection algorithm and then proceed with Kaggle dataset for detecting malignant tumors.

To help with the first part the authors of dataset have provided a tutorial on U-net segmentation. There is also a newer [Dense segmentation]() as discussed in the class. Some papers to get started are provided at Resourses link below the post and the post would be updated if some implementation is becomes available eventually. 
#TODO: research dense segmentation and provide code if available.

# K-means and mean shift clustering
