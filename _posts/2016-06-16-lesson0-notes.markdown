---
layout:     post
title:      "Fastai Course Summary: Lesson 0"
date:       2016-06-16 18:00:00
author:     "Apoorv Jagtap"
comment:	true
published:  true
category:	deeplearning
header-img: "images/fastai.png"
---

Since this the first post in the series, I would commence with recommending this course if you haven't already taken it (and if you have already began write a comment down below to work on group projects).

**Warning** : This course doesnot take a traditional approach and assumes some background knowledge. But the highlights of the course include practical approach from day 1 with all course materials available for free, [course notes](http://wiki.fast.ai/index.php/Course_notes), [course files](https://github.com/fastai/courses/tree/master/deeplearning1) and really helpful [forum](http://forums.fast.ai/) where even the course instructors participate regularly.

With that out of the way, we begin with [Lesson 0](http://course.fast.ai/lessons/lesson0.html) of [Deep Learning for Coder - Part 1](http://course.fast.ai/lessons/lessons.html), where Jeremy gives some idea of the state of machine learning and its potential impact. He also gives his introduction and [medical startup](https://www.enlitic.com/) he built around deep learning network ideas. If that's not inspiration enough then I don't know what is.

Anyways, the video continues explaining about neural networks which are basically a stack of layers learning something (which will become clear later) from the input provided in the form of images, text or any data. With this basic concept, Jeremy shows the famous approach used to deal with MNIST dataset, to visually see the differnt learnings of each layer from the image of handwritten digit passed as input.

Convolutional neural nets are commonly used in neural networks for dealing with images. To illustrate their working, he uses a simple matrix and an image of handwritten digit 7. Now he correlates these to matrices to output the results as shown below:



![]({{site.url}}/images/lesson0_matrix.png)


This exact approach is used in conv nets to detect edges, and many such matrices are employed for detecting other features (example: corners, curves), and deep layers are even able to detect objects as seen later in the course. You can play around with the matrices and see the different results. Now, instead of handcrafting these matrices they are randomly initialized and the goal is to update them to get the predicted output as close to the actual output. These matrices are called Kernels or filters and more information can be found on [Lesson Wiki](http://wiki.fast.ai/index.php/Lesson_0). A nice example with simple equation of a line is presented and solved with the help of neural network. The details are skipped here as I would want everyone to watch the video to get a better hang of what we will be learning and doing in this course.

This is a short video to kick things off, next lesson would be about setting up environment on your PC or AWS instance as detailed in the [next post](link coming soon).
