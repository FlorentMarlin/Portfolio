---
layout: post
title:  "Running App"
categories: jekyll update
image: /images/2024-07-29.png
---

Processing of running data

This study was performed to meet my personal needs.

<h3>Context</h3>

When running I use a heart-rate measuring chest-belt, and the associated Android app 'Polar Beat' from the maufacturer.

In my opinion, it is a very poor app, that provides hard-to-read graphs, and that does not allow any export.

![webjeda cards jekyll theme]({{site.baseurl}}/images/Screenshot_20240729_094902_Polar Beat.jpg)
<div class="mt20"></div>

![webjeda cards jekyll theme]({{site.baseurl}}/images/Screenshot_20240729_094913_Polar Beat.jpg)
<div class="mt20"></div>

I wanted to be able to draw conclusions from my running sessions, in terms of progression, and in terms of correlations.

<h3>Development</h3>

The personal processing of running data from the data relies on making screen captures on the phone of the two types of reports proposed by the app:
<ul class="list-group">
  <li class="list-group-item">Summary table</li>
  <li class="list-group-item">Curves of heart-rate and time-per-distance</li>
</ul>

<div class="mt20"></div>

Informations from the summary table were extracted using OCR, and aggregated in a Pandas Dataframe, in order to show the evolution of sessions.

Before any correlation could be made with respect to the heart-rate, the metric 'time-per-distance' was transformed into 'distance-per-time'.

Curves were separated and rebuilt using the pixel-map.

Curves were then smoothed to a usable resolution:

![webjeda cards jekyll theme]({{site.baseurl}}/images/2024-07-29.png)
<div class="mt20"></div>

<h3>Result</h3>

The superimposition of curves from different sessions allowed to view improvements in my performance.

The process is still tedious, as it relies on making screen captures on the phone.

The extent of conclusions to be drawn will always be limited in the absence of export of GPS-data.

<h3>Details</h3>

Following tools were notably used:
<ul class="list-group">
  <li class="list-group-item">Python</li>
  <li class="list-group-item">PIL</li>
  <li class="list-group-item">Pytesseract</li>
  <li class="list-group-item">Numpy</li>
  <li class="list-group-item">Pandas</li>
</ul>

