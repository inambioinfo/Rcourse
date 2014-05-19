# The codebook for run_analysis.R

## Testing environment:

* Mac OS X 10.9.2
* Firefox 29.0.1 (for downloading the data)
* Archive Utility v10.9.1 (for unzipping the data)
* RStudio version: 0.98.507
* R version: 3.1.0 GUI 1.64 Mavericks build (6734)
* packages: data.table V1.9.2

## Experimental study design:


Human Activity Recognition Using Smartphones Dataset
Version 1.0

Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.

Smartlab - Non Linear Complex Systems Laboratory

DITEN - Universit‡ degli Studi di Genova.

Via Opera Pia 11A, I-16145, Genoa, Italy.

activityrecognition@smartlab.ws

www.smartlab.ws


The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'UCI HAR Dataset/features_info.txt' for more details.

## Code book:

### features: 

(referring to 'UCI HAR Dataset/features_info.txt', modified).

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals TimeOfAcc-XYZ and TimeOfGyro-XYZ. These time domain signals  were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (TimeOfBodyAcc-XYZ and TimeOfGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz.

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (TimeOfBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (TimeOfBodyAccMag, TimeOfGravityAccMag, TimeOfBodyAccJerkMag, TimeOfBodyGyroMag, TimeOfBodyGyroJerkMag).

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing FourierTransformedBodyAcc-XYZ, FourierTransformedBodyAccJerk-XYZ, FourierTransformedBodyGyro-XYZ, FourierTransformedBodyAccJerkMag, FourierTransformedBodyGyroMag, FourierTransformedBodyGyroJerkMag.

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

* TimeOfBodyAcc-XYZ
* TimeOfGravityAcc-XYZ
* TimeOfBodyAccJerk-XYZ
* TimeOfBodyGyro-XYZ
* TimeOfBodyGyroJerk-XYZ
* TimeOfBodyAccMag
* TimeOfGravityAccMag
* TimeOfBodyAccJerkMag
* TimeOfBodyGyroMag
* TimeOfBodyGyroJerkMag
* FourierTransformedBodyAcc-XYZ
* FourierTransformedBodyAccJerk-XYZ
* FourierTransformedBodyGyro-XYZ
* FourierTransformedBodyAccMag
* FourierTransformedBodyAccJerkMag
* FourierTransformedBodyGyroMag
* FourierTransformedBodyGyroJerkMag

**NOTE:** In the original file, some features have double 'Body' in their names, such as 'FourierTransformedBodyBodyGyroJerkMag-std'. The script does not fix this possible error.

The set of variables that were estimated from these signals are: 

* mean: Mean value
* std: Standard deviation

    
### activities: 

Activities the subjects used to perform the experiment. Please refer to activity_labels.txt.

### subjects: 

identifiers of the subjects who carried out the experiment.

### mean: 

this is the average of each variable for each activity and each subject.

## Data processing:

1. Data downloaded from [link](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip), using "Firefox 29.0.1" (2014-05-15 14:51:29 IST).

2. zip file unzipped into folder "UCI HAR Dataset" with "Archive Utility v10.9.1".

3. In RStudio, the tables extracted from X_test.txt and X_train.txt are given column names from 1 to 561, corresponding the number of features.

4. The test and train 'X' tables are stacked, and merged with the feature table (extracted from features.txt). The names of the features are modified as the following:
    * 'f..' has been expanded to 'FourierTransformed..';
    * 't..' has been expanded to 'TimeOf..';
    * parentheses have been removed;
    * 'angle(variableA,variableB)' has been changed to 'angle.between.variableA.and.variableB'
    * Only features with 'mean' and 'std' are retained for further data processing. Else are discarded.

5. y_test/y_train tables (extracted from y_test.txt and y_train.txt) are merged with the activity table (extracted from activity_labels.txt), to give the numbers a meaningful replacement.

6. Merge subjects (extracted from subject_test.txt/subject_train.txt), values and features (both from the stacked 'X' tables), and activities (from the 'y' tables) to give comprehensive test.table and train.table.

7. Add a new 'group' column to both test.table and train.table, labeling them with 'test' and 'train', respectively.

8. Merge the two tables with 'rbind', to create a comprehensive data set. (test.table on top, train.table on bottom.)

9. Extract only 'mean' and 'std' features from the comprehensive data set, creating object 'mean.std.data'. Note that features with names as '..meanFreq' or 'angle.between...Mean.and...' are not included.

10. Create a second, independent tidy data set (tidy.data) with the average of each variable for each activity and each subject.

11. Write the tidy data to tidyData.csv under R's working directory.


