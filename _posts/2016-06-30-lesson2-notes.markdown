---
layout:     post
title:      "Our first Linear Model | FastAI Lesson 2"
date:       2016-06-30 18:00:00
author:     "Apoorv Jagtap"
comment:	false
published:  true
tags:	deeplearning fastai datascience software
header-img: "images/fastai.png"
---

> In the previous post [Lesson 1](), we breifly discussed about software and hardware setup for this 
> course, before building a simple model and explorting the concept of fine tuning. I highly recommend 
> going over it first if you haven't already.

Using the concepts from previous lesson we go further today and implement a neural network from scratch explaining the details.

1. Dogs vs Cats Redux submission to Kaggle

In the previous post we went over Dogs vs Cats competition to classify images between cats and dogs using VGG16 with the process of fine tuning.

[Dogs vs Cats Redux](https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/submissions) is a slight improvement to utilize the 'Kernel' features of Kaggle. The structure of the data provided is more suitable to the way Keras handles data to classify between images. Essentially, the images of cats and dogs are inside their respective folders in train, valid and sample folders. This helps to quickly train the model and test it for proper functioning. How its done in Jupyter notebook can be explored [here](https://github.com/fastai/courses/blob/master/deeplearning1/nbs/lesson2.ipynb) or follow the notebook provided with [course github](https://github.com/fastai/courses).

After setting up everything, execute the same lines of code as in previous lesson with the addition of saving weights for future reference. This is very handy as it saves the need for training the model over and over. At this point we can submit the results to Kaggle, follow the instructions below to do it from command line for easier workflow:

* Install Kaggle-cli tool from pip:		pip install kaggle-cli
* Configure the tool for the current competition:		kg config -g -u 'username' -p 'password' -c 'competition'
* Finally submit the results once they are ready using:		kg submit 'entry' -u 'username' -p 'password' -c 'competition' -m 'message'

You can also download the data from command line, for instructions use the [Wiki](http://wiki.fast.ai/index.php/Kaggle_CLI) although you need to accept the terms and conditions first so need to head over the Kaggle site anyway.

### Preparation of submission

Kaggle has very specific format for submission file and it has to be CSV which is as below:

id,	label
0,	0.07000
1200,	0.96000
35,	0.70000

The predictions using vgg.test are either 0 or 1, which need to be converted before submitting. This can be achieved use Numpy's clip function as demonstrated in notebook.

As a general pointer to keep in mind while submitting resutls to Kaggle is to check how they evaluate submissions. This is information is available on competition page and in our case its log loss function. So, in this case its better to convert our zeros to 0.02 and our ones to 0.98 or some similar values.

After your first submission you might wonder how do I improve my results. In the video Jeremy recommend fitting them more than once and slightly altering the learning rates as well.

The video goes over visualizing how the model is performing by looking at the results of how many it got right and how many it got wrong. He recommends following these 5 steps to check model perfomance:

1. A few correct labels at random
2. A few incorrect labels at random
3. The most correct lables of each class (those with highest probability that are correct)
4. The most incorrect labels of each class (those with highest probabiliy that are incorrect)
5. The most uncertain labels (those with probability close to 0.5)

### How does any neural network learn?

Before jumping into fine tuning, let's look at the layers of Convolutional Neural Network (CNN) to see what they learn when feed with images.

[An exceptional paper](https://arxiv.org/abs/1311.2901) by Matthew D Zeiler, Rob Fergus have explained in great detail. Here I will try to highlight the key points of their research:

1. The first layer of CNN learns primitive features in an image, like lines, edges.

### Note: add images

The above image shows that our first layer of CNN recognizes diagonal lines, solid lines.

With each layer they tend to learn more as shown in figure below. It seems to recognize simple shapes with door, window.


Deeper layers are able to even recognize objects as complex as face of animals. Understanding this is crucial since we need to have an intuition of what the model might learn at each layer and which layers should we keep for out problem. This can be better illustrated with a problem involving images that are not part of Imagenet dataset. Keeping all layers of VGG in this case won't be as effective. Instead the better approach might be to use only layers which are detecting primitive lines for example. 

In general try to visualize the output of each layer of your model to get better handle of what must be done to improve the results.

### Linear model from scratch

This was touched upon briefly in lesson 0, and is fundamental in understanding more complicated deep neural networks. Understanding linear model at an intuitive level would go a long way in understanding further content in this course.

We build this model in keras using these two lines:
	x = random((30,2))
	y = np.dot(x, [2.,3.]) + 1.
	
The first line initializes input vector of 2 dimension with 30 entries. Second line uses dot product between input and weight vector (where we have choose [2,3] as our weights). The results is added with 1 (Equation of straight line: y = mx + c).

With the input and output values set as above, our model needs to correctly find the weight vector and [1] (only x and y are given to our model).

A linear layer can be initialized in Keras using the Dense method. And for the neural network to use this layer (or any more layers you create), we need to wrap around these layers using Sequential method. This basicall tells us, this is our linear neural model with Dense as one of our layers.

	lm = Sequential([Dense(1, input_shape(2,))])
	lm.compile(optimizer=SGD(lr=0.1), loss='mse')
	
The model is then compiler with optimizer, to correct the randomly initialized weights with the goal of finally reaching as close to real weights as possible. Loss here is Mean Squared Loss which measures Euclidean distance between predicted output and real output.

The model is trained uisng fit method:

	lm.fit(x, y, nb_epoch=5, batch_size=1)
	lm.evaluate(x, y, verbose=0)
	
The results are close to our initial weights

This same approach can be used to classify between dogs and cats. First step would be to get the predictions using our pre-trained VGG model, which will give predictions between 1000 image classes. These prediction will serve as input to our linear model and output 2 classes for cats and dogs. Further step will be clear using the code given below:

### Note add code here

Model summary is very useful as it gives us an idea of the layers involved. In our case its just a single Dense layer.


One of the important part in neural network are the activation functions. These are non linear function which are used to active neurons in each layer of the network. We will learn about various activation functions throughout the course.

The following part would give a more clear idea on fine tuning a pre-trained network, in our case the VGG model. Lets us begin with the layers involved here.

	vgg.model.summary()
	




At the end, there is a dense layer which output probabilities of 1000 classes. To modify it for our case, all we need to do is remove this layer and set other layers as untrainable. What this does is allows us to utilize the pretrained weights but output only 2 classes.

To add this functionality we add a Dense to output only 2 classes.

	model.add(Dense(2, activation='softmax'))
	
As before setup our optimizer and fit the model with out cats vs dogs dataset.


That's all the fine tuning code in the previous post did. To get a better hang of it try with other datasets, fine tune multiple times to see the differences. Report your observations in the comment section below. 
