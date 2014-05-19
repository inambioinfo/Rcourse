# Rcourse

## Purpose

This is my work for the project of the Coursera course "Getting and Cleaning Data" [link](https://class.coursera.org/getdata-003)

## Introduction

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

[link](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

Here are the data for the project:

[link](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)(2014-05-15 14:51:29 IST)

In the R script called run_analysis.R that does the following.

* Merges the training and the test sets to create one data set.
* Extracts only the measurements on the mean and standard deviation for each measurement.
* Uses descriptive activity names to name the activities in the data set
* Appropriately labels the data set with descriptive activity names.
* Creates a second, independent tidy data set with the average of each variable for each activity and each subject.

## Testing environment:

* Mac OS X 10.9.2
* Firefox 29.0.1 (for downloading the data)
* Archive Utility v10.9.1 (for unzipping the data)
* RStudio version: 0.98.507
* R version: 3.1.0 GUI 1.64 Mavericks build (6734)
* packages: data.table V1.9.2

## How to use the script

* Download the data to the R working directory, from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip. (I used "Firefox 29.0.1" (2014-05-15 14:51:29 IST)).
* The zip file is unzipped into folder "UCI HAR Dataset" (I used "Archive Utility v10.9.1").

* In RStudio, run the "run_analysis.R".

* Your data will be saved as "tidyData.csv" under the R working directory.

It does not necessarily do the jobs in the order as listed. The reason is, in real life, I possibly need the data in another form. This is why I merge and change variable names before I trim the data. This is also why I wanted to add 'group' labels to the train and test data sets, which seems unnecessary for this project. But in the end, it does its job, I hope...

**NOTE**: I did not include the data in the "Inertial Signals" folders under "test" and "train" folders. Refer to this [link](https://class.coursera.org/getdata-003/forum/thread?thread_id=30) (alive as for 2014-05-18)