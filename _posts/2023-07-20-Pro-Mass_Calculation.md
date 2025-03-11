---
layout: post
title:  "Mass calculation"
categories: jekyll update
#image: /images/climate_occitanie_1.png
---

Automation of calculation for industry

This activity was performed in my positions as an engineer in the aerospace industry.


<h3>Context</h3>

My field of specialty in the aerospace design office was: fatigue and damage tolerance (i.e. accounting for the ageing of materials and for accidental damage during the lifetime of commercial aircrafts).

This has always been a data-intensive and time-consuming type of analysis, notably with the challenges of...

<ul class="list-group">
  <li class="list-group-item">Gathering a large set of diverse data for a given unitary study</li>
  <li class="list-group-item">Performing time-series analysis on long sequences, accounting for aircraft life</li>
</ul>

<div class="mt20"></div>


Historically, the main analysis process is formed by the two following steps:

<ul class="list-group">
  <li class="list-group-item">-1 - Finite Element Analysis to assess the distribution of stress in the aircraft structure - Using FEA software</li>
  <li class="list-group-item">-2 - Post-processing for Fatigue, specific to local location, basing on step -1- - Using Microsoft Excel</li>
</ul>

<div class="mt20"></div>


<h3>Motives and means</h3>

During my career, I have continuously strived to automate the step of analysis -2- above, basing notably on following programming languages:
<ul class="list-group">
  <li class="list-group-item">VBA - 2001-2006</li>
  <li class="list-group-item">C# - 2006-2013</li>
  <li class="list-group-item">Python - 2013-2023</li>
</ul>

<div class="mt20"></div>

In doing so, I allowed the interests of fellow analysts and companies to meet:
<ul class="list-group">
  <li class="list-group-item">Reduction of micro-tasks to be performed by human analysts</li>
  <li class="list-group-item">Increase in reliability of results</li>
  <li class="list-group-item">Increase in reproductibility of results</li>
  <li class="list-group-item">Reduction of analysis times</li>
  <li class="list-group-item">Keeping up with the increasing resolution of FEA-analysis, leading to larger sizes of data to manage</li>
</ul>

<div class="mt20"></div>

The following technologies allowed breakthroughs in the design of the analysis tools I developed:
<ul class="list-group">
  <li class="list-group-item">Object Oriented Programming (C#, Python)</li>
  <li class="list-group-item">Use of increasingly efficient databases (XML, JSON, SQLite)</li>
  <li class="list-group-item">Cross-platform interaction (Windows - Linux)</li>
  <li class="list-group-item">Table-based computation (Pandas)</li>
  <li class="list-group-item">Parallel computing</li>
  <li class="list-group-item">Surrogate models</li>
</ul>

<div class="mt20"></div>


I continuously tailored the tools I developed  to the company's HPC, to make use of the available capabilities in terms of parallel-computing and RAM.


<h3>Developments</h3>

Some noteworthy developments are detailed below:

<h5>Automated Fatigue analysis of riveting holes</h5>

The aim of this tool is to accelerate the prediction of crack initiation at riveting holes in an aircraft.

This is a highly time-consuming activity, as a single location typically requires a few hours analysis from a well-practised analyst.

As the automated process allows to reduce the analysis-time by a factor 100, this tool allows to have a vision of approximated margins for Fatigue on a large scale (i.e. dozens of thousands of locations) in the timeframe of one day.

No approximation is made by the tool.

This tool offers an improved rationale to identify the locations that might require a dedicated human analysis.


<h5>Automated Crack Propagation analysis in fuselage panels</h5>

The aim of this tool is to accelerate the prediction of crack growth in fuselage stiffened panels.

This tool notably combines three technologies:
<ul class="list-group">
  <li class="list-group-item">Automation of a sequence of steps with a decision tree</li>
  <li class="list-group-item">Parallel computing</li>
  <li class="list-group-item">Surrogate models</li>
</ul>

This tool allows to have a vision of approximated margins for Damage Tolerance for a 8m x 3m fuselage panel within 3 hours, whereas the generation of accurate margins requires a few days (and involving commercial software licence tokens).

The error-level associated with the prediction using Machine Leanring models was deemed manageable by analysts.

This tool offers an improved rationale to identify the locations that might require a dedicated human analysis.

This magnitude of execution time made it possible to rapidly iterate on the design, and opened the possibility for an automated optimization approach.

<h5>Automated Fatigue analysis of geometrical features</h5>

This family of tools go with the current trend to model the aircraft structure using a Finite Element Model, where the unitary element size is as small as 5mm.

They allow to automatically identify and analyze locations in the aircraft structure that are defined by a distinctive geometrical feature (change in thickness, cut-out, hole...), and that are in numbers ranging from a few dozens to a few hundreds of thousands.

The automated identification of specific geometrical features in the aircraft structure is made possible by storing the Finite Element mesh in a relational table.

The use of a table as a data-model additionally provides a means to efficiently perform mathematical operations on tables that have millions of rows.

The added value of this family of tools is to allow the systematical analysis of a very large number of locations, that used to be handled by the unit, after manual identification by the human analyst ... i.e. it unlocks a way of working that did not exist before.
