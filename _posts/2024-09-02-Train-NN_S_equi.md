---
layout: post
title:  "Neural Network for Stress Interpolation"
categories: jekyll update
image: /images/10081639.png
---

Benchmark of Deep Learning 

This study was performed as part my self-training for Deep Learning.

<h1>Context</h1>

The structural analysis of aircraft components involves the use of specific criteria for the fatigue (i.e. aging) of metallic parts.
For flat/thin components, this requires the prediction of the direction and magnitude of the maximum fatigue damage, in a 2D-plane.
This numerical analysis is performed at millions of locations for a given aircraft design, and is CPU- and time-consuming, and may be subject to software licence costs.
I proposed that the number of unit calculations could be reduced, using regression, for shorter times and lower costs.
The typical approach is to perform 18 unit-calculations, along 18 directions/angles separated by 10 degrees.

The typical shapes of the evolution of damage-criterion vs. angle fall into the following two categories:

<div class="mt20"></div>

![webjeda cards jekyll theme]({{site.baseurl}}/images/13470070.png)
<div class="mt20"></div>

![webjeda cards jekyll theme]({{site.baseurl}}/images/10081639.png)
<div class="mt20"></div>

The question was whether the complete set of results: criterion vs. angle could be inferred by a limited set of known values (e.g. 3), i.e. whether a whole curve (size=18) could be derived from 3 supporting values.


<h1>Development</h1>

The database consisted in approx. 100 000 curves.

A Neural Network was trained, with tuning of its hyperparameters.

On the images above, the filled-curves are the target values, while the 15 markers are the values predicted by the model, basing on the not-shown 3 supporting values at angles [50, 90, 140].

<h1>Result</h1>

The model is successful at predicting the direction and magnitude of the maximum fatigue damage, with a 5% error.

Since the aircraft industry is rightly wary of approximation-tools, for the sake of safety, predictions used for A/C certification will not be based on a model.
Therefore a three-step approach can be proposed:

<ol class="list-group">
  <li class="list-group-item">Perform the official/accurate calculation for three directions</li>
  <li class="list-group-item">Use the model to infer the whole set of results and predict the highest values of the fatigue-criterion</li>
  <li class="list-group-item">Identify the aircraft critical locations in erms of fatigue criterion</li>
  <li class="list-group-item">Perform the official/accurate calculation for the critical locations</li>
</ol>

<div class="mt20"></div>

The present POC shows the potential for a reduction of time and cost by a factor 6, at the expense of setting-up a multi-step approach involving a regression-model.

<h1>Details</h1>

The following ressources were notably studied:
<ul class="list-group">
  <li class="list-group-item">'Python for Data Science and Machine Learning Bootcamp' - Udemy</li>
  <li class="list-group-item">'Hands-on Machine Learning with Scikit-learn and TensorFlow' - Aurélien Géron</li>
</ul>

<div class="mt20"></div>

Following tools were used:
<ul class="list-group">
  <li class="list-group-item">Python</li>
  <li class="list-group-item">Scikit-Learn</li>
  <li class="list-group-item">Tensor Flow</li>
</ul>
