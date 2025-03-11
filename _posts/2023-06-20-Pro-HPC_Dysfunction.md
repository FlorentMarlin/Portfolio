---
layout: post
title:  "Analysis of HPC Performance"
categories: jekyll update
#image: /images/climate_occitanie_1.png
---

Analysis of HPC dysfunction for industry

This activity was performed in my position as an engineer in the aerospace industry.


<h3>Context</h3>

Unitary tasks of numerical analysis, were submitted to the HPC (High Performance Cluster) as jobs for a LSF queueing system.

It appeared that a proportion of submitted jobs, basing on Python-code written by my team, were not processed, i.e. were marked as 'exited', while not being executed not errored.

This hindered the activity of structural engineers, who had to submit repeatedly their jobs before they were actually processed.

The IT-department initially shifted the blame on the Python code.

<h3>Developments</h3>

I modified the code to be submitted to HPC to log the status of execution at different stages of the process.

I then processed the logs using time-series approaches, and came up with statistics of malfunction occurrence.

I modified the code to be submitted to HPC... to the bare minimum that made appear the dysfunction of the HPC, hence developing a unit test.

<h3>Result</h3>

The outcome of the analysis was shared with the IT-department, who acknowledged the issue.

The unit test was shared with the IT-department, so that IT could run it autonomously, in their endeavour to solve the problem.


<h3>Details</h3>

Following tools were used:
<ul class="list-group">
  <li class="list-group-item">Python</li>
  <li class="list-group-item">Pandas</li>
</ul>
