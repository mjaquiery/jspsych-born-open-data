---
title: Fetching the Data
teaching: 5
exercises: 20
questions: []
objectives:
  - Retrieve our OSF data for use.
keypoints:
  - The OSF API exposes the public data for us.
  - We access the data just like anyone else, without having to log in.
day: 1
order: 700000
missingDependencies: []
dependencies: []
originalRepository: mjaquiery/ukrn-test-workshop
summary: We'll view our data in an R project using RStudio Cloud plus the OSFr package.

---

## Accessing using OSFr in R

The first step is to sign into RStudio Cloud using your GitHub account.
* Go to [https://rstudio.cloud/](https://rstudio.cloud/) and click 'Get Started for Free'
![RStudio Cloud login screenshot](../fig/rstudio-get-started.jpg)
    * Sign up for the free account level
    ![RStudio Cloud sign up screenshot](../fig/rstudio-sign-up.jpg)
    * And then select 'Sign up with GitHub Account'
    ![RStudio Cloud sign up with GitHub screenshot](../fig/rstudio-github-sign-up.jpg)
    * Sign into GitHub, and authorize the RStudio Cloud application

Now you've created an RStudio Cloud account, you can clone the example OSFr project and use it to access your data.
* Select 'New Project from Git Repository'
![RStudio Cloud create project from repository screenshot](../fig/rstudio-new-project.jpg)
   * Enter `https://github.com/UKRN-Open-Research/OSFr-example.git` and click 'OK'
   ![RStudio Cloud create project form screenshot](../fig/rstudio-github-url.jpg)
   * Wait while the project loads

To execute the project, we need to install the packages it depends on.
Because the project uses the `renv` package to manage packages, we can install all the required packages by entering `renv::restore()` in the console and pressing `[ENTER]`.
It will take a little while for the packages to install.
![RStudio Cloud renv::restore() screenshot](../fig/rstudio-restore-open.jpg)
We then click on `download_data.R` to open that file.
We'll see that it opens as a pane in the top-left of the screen.

* We need to tell the script where to find our files.
This is done by changing the `osf_component` variable (line 3) to be our component id we made a note of earlier.
![RStudio Cloud source screenshot](../fig/rstudio-source.jpg)
    * When the `osf_component` is updated, run the script by clicking the 'source' button in the top pane.
    * Once the script has run, you can find your data in the `raw_data` directory in the files pane (bottom-right)

## Downloading as .zip

You can also download your data directly from the OSF as a .zip (or as individual .csv files).

This is as simple as going to your project in the OSF, selecting the OSF Storage in the Files browser pane, and clicking the 'Download as zip' button.
![OSF download as .zip screenshot](../fig/osf-download.jpg)

> ## Note:
> At no point in these process did we tell the R script (or need to tell the web browser) who we were.
> The data are public, and can be accessed easily and immediately by anyone, including ourselves.
>
> We can even write our analysis scripts to download the raw data each time, and thus track the raw data all the way to the figures and statistics we eventually produce for publication.
{: .callout}
