---
layout: post
title:  "NN for Regression"
categories: jekyll update
image: /images/SIF_TF.png
---

Benchmark of Deep Learning for industry

This study was performed as part my self-training for Deep Learning.

<h3>Context</h3>

The structural analysis of aircraft components involves the prediction of crack growth in metallic parts of the fuselage.

The prediction is particularly challenging for fuselage panels, where the crak growth is defined by the interaction of several aircraft components (skin and stiffeners).

This numerical analysis is highly time-consuming, and is subject to software licence costs.

The following two carpet-plots show typical evolutions of the metric driving crack propagation (Stress Intensity Factor vs. crack length):

<div class="mt20"></div>

![webjeda cards jekyll theme]({{site.baseurl}}/images/SIF_TF.png)
<div class="mt20"></div>

![webjeda cards jekyll theme]({{site.baseurl}}/images/SIF_RC.png)
<div class="mt20"></div>

During my time at Airbus, I implemented approximation-tools based on Gaussian models of the Scikit-Learn Machine Learning library, with great success already.

As part of my self-training, I wanted to investigate the performance of a neural network based approach for the same purpose.


<h3>Development</h3>

The training set consisted in approx. 5 000 curves.

A Neural Network was trained, with tuning of its hyperparameters.

On the images above, the filled black curves are the target values, while the colored interpolated curves are predicted by the model.

<h3>Result</h3>

The model is successful at predicting the crack propagation metric, with a 5% error (this translates into 20% error in terms of number of aircraft flights), and it deemed manageable by stress engineers. 

In comparison to the prior approach based on Machine Learning, the neural network based model...
<ul class="list-group">
  <li class="list-group-item">... is less sensitive to the uneven curves of the training dataset </li>
  <li class="list-group-item">... serializes in a very small files, making deployment much smoother</li>
  <li class="list-group-item">... is able to handle the complete shape of the curve, whereas the Gaussian model involved splitting the curve into two portions</li>
</ul>


<h3>Details</h3>

The following ressources were notably studied:
<ul class="list-group">
  <li class="list-group-item">'Python for Data Science and Machine Learning Bootcamp' - Udemy</li>
  <li class="list-group-item">'Hands-on Machine Learning with Scikit-learn and TensorFlow' - Aurélien Géron</li>
</ul>

<div class="mt20"></div>

Following tools were used:
<ul class="list-group">
  <li class="list-group-item">Python</li>
  <li class="list-group-item">Pandas</li>
  <li class="list-group-item">Scikit-Learn</li>
  <li class="list-group-item">Tensor Flow</li>
</ul>
