---
layout: post
title:  "RNN for rivers"
categories: jekyll update
image: /images/RNN.png
---

Benchmark of Deep Learning for climate

This study was performed as part my self-training for Deep Learning.

<h3>Context</h3>

My parent's house is located next to a watercourse that is regularly subject to overflows, so that gardens are flooded approx. 20 days per year.

In 2016 houses of the whole county were flooded with catastrophical consequences.

As part of my self-training, I wanted to investigate the prediction of watercourse flow/height, basing on downpour and soil wetness data.


<h3>Development</h3>

The training set consisted in readings for one weather station and one flow sensor, over a period of 8 years.

Prior to the training of the model, the following aspects were investigated:
<ul class="list-group">
  <li class="list-group-item">The requirement for smoothing the input data for downpour</li>
  <li class="list-group-item">The requirement for time-shifting inputs (as 20 hours separate, as an average, an event of downpour at the weather station from the increase of the water flow at the measurement station downstream)</li>
</ul>

<div class="mt20"></div>

A Recurrent Neural Network was trained, with tuning of its hyperparameters (in particular, the length of the sequences is of importance).

<h3>Result</h3>

The model demonstrates interesting response in terms of increase of water flow vs. episodes of rain.

The prediction obtained for year 2024, basing on preceding years, is shown below:

![webjeda cards jekyll theme]({{site.baseurl}}/images/RNN.png)
<div class="mt20"></div>

<ul class="list-group">
  <li class="list-group-item">Blue curve: Target water flow rate</li>
  <li class="list-group-item">Red curve: Predicted water flow rate</li>
  <li class="list-group-item">Green curve: Downpour</li>
</ul>

<div class="mt20"></div>

However, the current model is still lacking, in that, at the end of summer, it predicts increased flow rate following heavy rain episodes, while no high water activity was actually measured.

<h3>Way Forward</h3>

<ul class="list-group">
  <li class="list-group-item">Perform data analysis on past years to identify human action on watercourse activity, and that may interfere with the present study</li>
  <li class="list-group-item">Be more knowledgeable on RNN parameters</li>
  <li class="list-group-item">Base the model on a more conventional watercourse (i.e. river vs. joining-canal)</li>
</ul>

<div class="mt20"></div>

<h3>Details</h3>

The following ressources were notably studied:
<ul class="list-group">
  <li class="list-group-item">'Python for Data Science and Machine Learning Bootcamp' - Udemy</li>
  <li class="list-group-item">'Hands-on Machine Learning with Scikit-learn and TensorFlow' - Aurélien Géron</li>
  <li class="list-group-item">TensorFlow.org Tutorial - Time series forecasting</li>
  <li class="list-group-item">Stackoverflow.com</li>
</ul>

<div class="mt20"></div>

Following tools were used:
<ul class="list-group">
  <li class="list-group-item">Python</li>
  <li class="list-group-item">Pandas</li>
  <li class="list-group-item">Scikit-Learn</li>
  <li class="list-group-item">Tensor Flow</li>
</ul>