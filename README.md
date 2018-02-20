Getting and Cleaning Data: Course Project
###########################################3
The R script called run_analysis.R does the following steps:---

Merges the training and the test sets to create one data set.
Extracts only the measurements on the mean and standard deviation for each measurement.
Uses descriptive activity names to name the activities in the data set
Appropriately labels the data set with descriptive activity names.
Creates a second, independent tidy data set with the average of each variable for each activity and each subject.

################################
Description of steps:-

A few steps were taken to transform the initial data set. The test and train sets have were merged and the subject identifiers and activity labels were pulled in to create a single data set. The activity identifiers were translated from identifiers into human-readable names. Only the mean and standard deviation variables were kept. Those variables were further summarized by taking their mean for each subject/activity pair. The data is in "wide" format as described by Wickham; there is a single row for each subject/activity pair, and a single column for each measurement.

The final data set can be found in the tidy.txt file, which can be read into R with read.table("tidy.txt", header = TRUE). A detailed description of the variables can be found in CodeBook.md. The basic naming convention is:

###################################3
run_analysis.R

The script was implemented under Microsoft Windows 10 and RStudio. It was not tested under any *nix environment nor the command-line version of R. Please run it from RStudio. Be aware that the script takes about 5 minutes to complete all the steps, including downloading the original dataset, on a Core i7 laptop and a ~15Mbit/s ADSL.

The script performs the following high-level tasks:

Prepares the R dependencies and the working directories
Downloads and unzip the original dataset (if not already present)
Loads the features, keeps only the variable related to mean and std
Loads the subjects and activities. It merges them.
It merges features, subjects, and activities
Cleans the variable names to human readable form (and R coding standard compliant)
Creates the tiny data set with the average of each variable for each activity and each subject.
Please note that the steps are documented at a deeper level in CodeBook.md.

CodeBook.md

The CodeBook contains a description of the original dataset, the data acquisition process, the data transformation process, the variables, and the tidy dataset format.
