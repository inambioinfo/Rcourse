# The codebook for run_analysis.R

## Testing environment:

* Mac OS X 10.9.2
* Firefox 29.0.1 (for downloading the data)
* Archive Utility v10.9.1 (for unzipping the data)
* RStudio version: 0.98.507
* R version: 3.1.0 GUI 1.64 Mavericks build (6734)
* packages: data.table V1.9.2



## Variables:

* features: please refer to 'UCI HAR Dataset/features_info.txt'. 
    * 'f..' has been expanded to 'FourierTransformed..';
    * 't..' has been expanded to 'TimeOf..';
    * parentheses have been removed;
    * 'angle(variableA,variableB)' has been changed to 'angle.between.variableA.and.variableB'
    * Only features with 'mean' and 'std' are retained for further data processing. Else are discarded.
    
* activities: please refer to activity_labels.txt. 

* subjects: identifiers of the subjects who carried out the experiment.

* mean: this is the average of each variable for each activity and each subject.

## Data processing:

1. Data downloaded from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip, using "Firefox 29.0.1" (2014-05-15 14:51:29 IST).

2. zip file unzipped into folder "UCI HAR Dataset" with "Archive Utility v10.9.1".

3. In RStudio, the tables extracted from X_test.txt and X_train.txt are given column names from 1 to 561, corresponding the number of features.

4. The test and train 'X' tables are stacked, and merged with the feature table (extracted from features.txt). The names of the features are modified as mentioned above.

5. y_test/y_train tables (extracted from y_test.txt and y_train.txt) are merged with the activity table (extracted from activity_labels.txt), to give the numbers a meaningful replacement.

6. Merge subjects (extracted from subject_test.txt/subject_train.txt), values and features (both from the stacked 'X' tables), and activities (from the 'y' tables) to give comprehensive test.table and train.table.

7. Add a new 'group' column to both test.table and train.table, labeling them with 'test' and 'train', respectively.

8. Merge the two tables with 'rbind', to create a comprehensive data set. (test.table on top, train.table on bottom.)

9. Extract only 'mean' and 'std' features from the comprehensive data set, creating object 'mean.std.data'. Note that features with names as '..meanFreq' or 'angle.between...Mean.and...' are not included.

10. Create a second, independent tidy data set (tidy.data) with the average of each variable for each activity and each subject.

11. Write the tidy data to tidyData.csv under R's working directory.


