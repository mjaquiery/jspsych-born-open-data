---
title: Applying to Your Own Workflow
teaching: 10
exercises: 180
questions:
  - When will I check data licensing for a project?
  - When will I implement data saving?
objectives:
  - Implement what we've learned into our own workflow.
keypoints: []
day: 1
order: 800000
missingDependencies: []
dependencies: []
originalRepository: mjaquiery/ukrn-test-workshop
summary: We have a large block of time dedicated to implementing born open data saving into your own project. The instructors and helpers will be around to answer questions and help with any issues you run into.

---

## Putting it to Use

The goal of today is to leave with a workflow which implements born open data in your own workflow, and with an understanding of how to implement this into your other projects as they are developed.

For this session, you'll need a project of your own - perhaps one of:
* A copy of a recent project where you've already collected data
* A project currently under development

You'll work at your own pace, with support from your peers and the workshop instructors and helpers to implement a born open workflow in your project.
There are some points below for reference:

### Creating an OSF Project and Component

* Make sure you have a dedicated component for the data
* Set the data storage region to `Germany - Frankfurt`
* You can set its license/visibility separately to the main project

* You can create a DOI so you can cite your data easily

### Creating an OSF PAT

* `username` > `settings` > `Personal access tokens`
* Make sure your token has the `osf.nodes.data_write` scope

### Writing the save data scripts

* The participant's computer runs the study
* Then sends the data to your server for saving
* The server uses the OSF API to upload the data

* Add `secrets.php` or whichever other file you use to store your PAT to your `.gitignore` file so you don't upload your PAT to GitHub!

* Separate public from private data!
    * Private data might be Prolific/MTurk participant IDs
    * Any free-text responses

> ## Don't call the OSF from the participant's computer!
> To upload data to the OSF, you need your personal access token.
> If you have the participant's computer upload the data, you'll have to give your participants your PAT.
> Exposing your PAT like this means the participant could write any data they wanted to any of your OSF projects! **This is very bad**.
>
> Instead, have the participant send the data to your server, and send the data from your server to the OSF.
{: .solution}

### Data dictionary
* Variable
* (friendly) Name
* Type
* Description

* Save as `data_dictionary.csv` and upload to your data component storage

### Testing!

* Complete your experiment (or a trial version) and ensure the data upload successfully.
* Make sure you let the participant know if something goes wrong.

### Best practice

* Test saving data before you let participants begin the experiment.
* Include useful error messages when things go wrong so participants can help you debug errors.
* Give participants an alternate way of providing their data if you fail to upload automatically (e.g. output a text box with the CSV data they can copy+paste into an email to you)

* As a bonus: why not provide participants with a link to see their data on the OSF?

