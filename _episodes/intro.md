---
title: Introduction
teaching: 10
exercises: 5
questions:
  - What is 'born open' data?
  - Why should data be 'born open'?
objectives:
  - Understand how to access resources, ask for help, and give feedback.
  - Understand what the workshop will contain.
keypoints:
  - "'Born open' means that data are saved to a publicly-accessible location as
    they are collected."
  - "'Born open' data are accessed by the researcher who collects the data in
    the same way that they are accessed by the public."
day: 1
order: 100000
missingDependencies: []
dependencies: []
originalRepository: mjaquiery/ukrn-test-workshop
summary: A friendly welcome to the workshop, a little bit of housekeeping, and
  an overview of what we'll be doing.

---
> ## Things You’ll Need To Complete This Tutorial
> #### A Webserver or Website for Online Behavioural Experiements
> This workshop focusses on implementing a born open workflow for jsPsych online experiments.
> Other kinds of online experiments will work well enough, but may take some time for us to help you implement.
> Having a webserver capable of running PHP scripts will help in following the example section of the workshop.
>
> If you do not have a webserver, install XAMPP using the instructions
> in the on the [homepage]({{ "/" | relative_url }}).
{: .prereq}

Today we will be implementing a 'born open' workflow for our data collection.
This will mean that the data we collect will be saved into a publicly-accessible repository at the time we collect it, and when we want to access it we will do so in the same way that other researchers will.
We will do our best to ensure that our data is in line with the [FAIR sharing principles](https://www.go-fair.org/fair-principles/):
* **F**indable
  * The data will be saved on the [OSF](https://osf.io/), where we can give them a DOI
* **A**ccessible
  * We will access our data using the same public OSF interface as everyone else
* **I**nteroperable
  * We will save data in .csv format so that it can be loaded by many different programs
* and **R**eusable
  * By giving our data an appropriate license, we will ensure people are clear about how the data can be used
  * By supplying a data dictionary which explains the variables, we will make it possible for others to understand our dataset

> ## Discussion time
> - Who has tried to use shared data before?
>   - What was the experience like?
{: .challenge}

#### Overview

First, we'll work through toy example where we adapt the [jsPsych quickstart project](https://github.com/mjaquiery/jsPsych-quickstart) to save data automatically to an OSF project component.
We will cover:
* Cloning or copying the jsPsych quickstart project
* Setting up an OSF project component to house the data
* Setting up an OSF Personal Access Token to authorise saving the data
* Adapting the participant-side file (`index.html`) to add a participant id and send data to the server
* Creating a server-side file (`save_data.php`) to send the data to the OSF

Later, we'll have a block of time for you to create a version of one of your current projects which saves to the OSF.
We will be here to give you as much help as you need.
