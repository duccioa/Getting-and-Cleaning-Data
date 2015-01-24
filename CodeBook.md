CodeBook for the tidy dataset - Getting and Cleaning Data: Course Project
=========================================================================

Data source
-----------
This dataset is obtained from the "Human Activity Recognition Using Smartphones Data Set" which can be downloaded from: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
Derived data for the project are available at: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

Data merge
----------
Train and test data sets are merged to create one data set stored in mergedData.
Train data set contains data from three files: train\X_train.txt, train\y_train.txt and train\subject_train.txt.
The same holds for the test set. Test files are test\X_test.txt, test\y_test.txt and test\subject_test.txt.

Feature Selection 
-----------------
As I mentioned in the README.md, the file features.txt contains labels for test and train data sets.
Our task is to select only measurements that contains words like mean or standard deviation (std).

I used built-in grep function with parameters ".*Mean.*|.*Std.*" and ignore.case = TRUE to select also labels like tBodyAcc-mean()-X.

List of selected measurements:

tBodyAcc-mean()-X, tBodyAcc-mean()-Y, tBodyAcc-mean()-Z,
tBodyAcc-std()-X, tBodyAcc-std()-Y, tBodyAcc-std()-Z,
tGravityAcc-mean()-X, tGravityAcc-mean()-Y, tGravityAcc-mean()-Z,
tGravityAcc-std()-X, tGravityAcc-std()-Y, tGravityAcc-std()-Z,
tBodyAccJerk-mean()-X, tBodyAccJerk-mean()-Y, tBodyAccJerk-mean()-Z,
tBodyAccJerk-std()-X, tBodyAccJerk-std()-Y, tBodyAccJerk-std()-Z,
tBodyGyro-mean()-X, tBodyGyro-mean()-Y, tBodyGyro-mean()-Z,  
tBodyGyro-std()-X, tBodyGyro-std()-Y, tBodyGyro-std()-Z,    
tBodyGyroJerk-mean()-X, tBodyGyroJerk-mean()-Y , tBodyGyroJerk-mean()-Z,
tBodyGyroJerk-std()-X, tBodyGyroJerk-std()-Y, tBodyGyroJerk-std()-Z,
tBodyAccMag-mean(), tBodyAccMag-std(), tGravityAccMag-mean(), 
tGravityAccMag-std(), tBodyAccJerkMag-mean(), tBodyAccJerkMag-std(),
tBodyGyroMag-mean(), tBodyGyroMag-std(), tBodyGyroJerkMag-mean(), 
tBodyGyroJerkMag-std(), fBodyAcc-mean()-X, fBodyAcc-mean()-Y,    
fBodyAcc-mean()-Z, fBodyAcc-std()-X, fBodyAcc-std()-Y,     
fBodyAcc-std()-Z, fBodyAcc-meanFreq()-X, fBodyAcc-meanFreq()-Y,
fBodyAcc-meanFreq()-Z, fBodyAccJerk-mean()-X, fBodyAccJerk-mean()-Y, 
fBodyAccJerk-mean()-Z, fBodyAccJerk-std()-X, fBodyAccJerk-std()-Y, 
fBodyAccJerk-std()-Z, fBodyAccJerk-meanFreq()-X, fBodyAccJerk-meanFreq()-Y, 
fBodyAccJerk-meanFreq()-Z, fBodyGyro-mean()-X, fBodyGyro-mean()-Y,   
fBodyGyro-mean()-Z, fBodyGyro-std()-X, fBodyGyro-std()-Y,     
fBodyGyro-std()-Z, fBodyGyro-meanFreq()-X, fBodyGyro-meanFreq()-Y, 
fBodyGyro-meanFreq()-Z, fBodyAccMag-mean(),fBodyAccMag-std(), 
fBodyAccMag-meanFreq(), fBodyBodyAccJerkMag-mean(), fBodyBodyAccJerkMag-std(), 
fBodyBodyGyroMag-mean(), fBodyBodyGyroMag-std(), fBodyBodyGyroMag-meanFreq(), 
fBodyBodyGyroJerkMag-mean(), fBodyBodyGyroJerkMag-std(), fBodyBodyGyroJerkMag-meanFreq(), 
fBodyBodyAccJerkMag-meanFreq().

Other vectors used in the angle() measurement:
angle(tBodyAccMean,gravity), angle(tBodyAccJerkMean), gravityMean), 
angle(tBodyGyroMean,gravityMean), angle(tBodyGyroJerkMean,gravityMean), 
angle(X,gravityMean), angle(Y,gravityMean), angle(Z,gravityMean).

Name activities
---------------
Activity names are load from file activity_labels.txt. There are 6:
WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING.
Each value has a numeric ID which correspondences to the ID in column 'Activity' in the tidy data set.
These numeric values are replaced by corresponding activity name.

Label names for data set tidy:
------------------------------
Subject: ID of a subject performing activity. Range of values [1:30].
Activity: Name of performed activity (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING).

Rest of the columns correspond to averaged variables describing mean/std measurements of each variable for each activity and each subject. 
Names of these variables are same as in the features.txt E.g. tBodyAcc-mean()-X, tBodyAcc-mean()-Y, tBodyAcc-mean()-Z.
	
Save results:
-------------
Results are kept in data set tidy. Script writes this data to text file tidy.txt.