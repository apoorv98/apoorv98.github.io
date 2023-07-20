---
layout:     post
title:      "Fastai Course Summary: Lesson 1"
date:       2016-06-23 18:00:00
author:     "Apoorv Jagtap"
comment:	true
published:	true
header-img: "images/fastai.png"
---

> There is [Lesson 0](), please check it out first so you don't miss anything.
> There I have mentioned some important links and purpose of this course.
> Without further ado let's get into the content for this post.

Use the links below to jump to section you need more information about:

1. [Software and Hardware Setup](#software-and-hardware-setup)
2. [Kaggle Cats vs Dogs data setup](#kaggle-cats-vs-dogs-data-setup)
3. [Pre-trained model and finetuning](#pre-trained-model-and-finetuning)

### Software and Hardware Setup
It is no surprise that we need programming languages and frameworks to write the necessary code along with supporting hardware.

Lets begin with hardware, it is recommended to use a system with GPU access in general for deep learning. Although, from my experience it is not a hard requirement if you (like me) are only going to test on small dataset. In fact, I would highly recommend using this approach first to get a hang of the work flow, concepts and when your script is finally complete are ready to run on entire dataset switch to AWS. Speaking of AWS, Jeremy has provided another video to help with the process, linked [here](https://www.youtube.com/watch?v=8rjRfW4JM2I). I would also recommend reading the [Course Wiki for AWS setup](http://wiki.fast.ai/index.php/AWS_install) as it lists common problems reported on forum and the solution to handle the issues. If you face any more problems with this part use this [forum](http://forums.fast.ai/) to ask any question and there will be people to help out. 

For the software part, I would recommend installing [Anaconda](https://docs.continuum.io/anaconda/install) especially for a person with little software knowledge as it installs all the required components to get started. For more advanced user, basically we need to install [Numpy](), python package for matrix computation, [Keras](), deep learning library for Python and [Jupyter notebook](), if you want to follow exactly as demonstrated in the videos. Apart from these, there are course specific files required which can be found on [github repo]() of the course. For pre-trained model and weights, use this [link](). I would recommend cloning the repo and updating it as required. More details on how all the software packages and framework work are explained in the video.

### Kaggle Cats vs Dogs data setup
For this lesson, we will be using [Kaggle's Dogs Vs Cats dataset]() to classify images. Simply download the data from the link provided and use the provided notebook to follow the course. Even before watching the video, I would recommend going through [Using provided notebook](http://wiki.fast.ai/index.php/How_to_use_the_Provided_Notebooks) to get most out of the course. Personally, I watched the video once, tried to implement the code myself (going back to provided notebook once I got stuck) and watched the video again to better understand the concepts. 

### Pre-trained model and finetuning
Now that the data is ready, we need a model which uses some algorithm to learn from the data and output the results we want, this is basically what we will be doing in deep learning.

Here we are using pre-trained model call VGG16. Why? VGG16 is a convolutional neural network model trained on Imagenet Dataset. **Remember**: we generally use convolutional type neural network when dealing with images. Imagenet dataset contains thousands of images and we can leverage the training performed here be improve the accuracy of our results. The only caveat is VGG16 was designed to output 1000 categories (and not just cats and dogs), since there were 1000 categories on Imagenet.

This is where the concept of finetuning comes in. To make VGG16 output just 2 categories (as required in our case), we provide the model with just two categories as input (this is done during the data setup where we put the images in two folders labeled cats and dogs in sample, train and valid directories).

Snapshot of the code used to obtain results is given below:

![](../images/lesson1_code.png)

The images are given in batches, as is normally the case in deep learning. You can try changing the nb_epoch to see if the accuracy increase any further. This model gives more than 90% accuracy with just these lines of code. Further details of underlying code is given in further lessons or inquisite users can explore the util.py and vgg16.py files.

Next lesson will continue with these basic ideas and expand them further, so read along [here]().
