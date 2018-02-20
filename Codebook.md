
About UCI HAR Dataset-

'README.txt'

'features_info.txt': Shows information about the variables used on the feature vector.

'features.txt': List of all features.

'activity_labels.txt': Links the class labels with their activity name.

'train/X_train.txt': Training set.

'train/y_train.txt': Training labels.

'test/X_test.txt': Test set.

'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent. 

 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. 
                             Its range is from 1 to 30. 

'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in 
                  standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for
                                  the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 

'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from 
                                                the total acceleration. 
 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. 
                                                 The units are radians/second. 

Analysis process

The analysis script, run_analysis.R reads in the processed experiment data and performs a number of steps to
get it into summary form.Both the processed test and training datasets are read in and merged into one data frame.
The data columns are then given names based on the features.txt file.
Columns that hold mean or standard deviation measurements are selected from the dataset,
while the other measurement columns are excluded from the rest of the analysis.
The activity identifiers are replaced with the activity labels based on the activity_labels.txt file.
Invalid characters (() and - in this case) are removed from the column names. Also, duplicate phrase BodyBody in some columns names is replaced with Body.
The data is then grouped by subject and activity, and the mean is calculated for every measurement column.
Finally, the summary dataset is written to a file, run_data_summary.txt.
Each line in run_analysis.R is commented. Reference the file for more information on this process.

#################
Columns in output file

The columns included in the output file are listed below:

subject_id - The id of the experiment participant.
activity_labels - The name of the activity that the measurements correspond to, like LAYING or WALKING.

All of the following fields represent the mean of recorded data points for the given subject and activity. 
Libraries Used

#################
The libraries used in this operation are data.table and dplyr. We prefer data.table as it is efficient in handling large data as tables. dplyr is used to aggregate variables to create the tidy data.

library(data.table)
library(dplyr)
#######################
The detailed description of the different measurement types can be found in the features_info.txt file included in the data zip file.

tBodyAcc_mean_X
tBodyAcc_mean_Y
tBodyAcc_mean_Z
tGravityAcc_mean_X
tGravityAcc_mean_Y
tGravityAcc_mean_Z
tBodyAccJerk_mean_X
tBodyAccJerk_mean_Y
tBodyAccJerk_mean_Z
tBodyGyro_mean_X
tBodyGyro_mean_Y
tBodyGyro_mean_Z
tBodyGyroJerk_mean_X
tBodyGyroJerk_mean_Y
tBodyGyroJerk_mean_Z
tBodyAccMag_mean
tGravityAccMag_mean
tBodyAccJerkMag_mean
tBodyGyroMag_mean
tBodyGyroJerkMag_mean
fBodyAcc_mean_X
fBodyAcc_mean_Y

Names of the variables in extractedData after they are edited are following:-
[1] "TimeBodyAccelerometerMean()-X"                    
##  [2] "TimeBodyAccelerometerMean()-Y"                    
##  [3] "TimeBodyAccelerometerMean()-Z"                    
##  [4] "TimeBodyAccelerometerSTD()-X"                     
##  [5] "TimeBodyAccelerometerSTD()-Y"                     
##  [6] "TimeBodyAccelerometerSTD()-Z"                     
##  [7] "TimeGravityAccelerometerMean()-X"                 
##  [8] "TimeGravityAccelerometerMean()-Y"                 
##  [9] "TimeGravityAccelerometerMean()-Z"                 
## [10] "TimeGravityAccelerometerSTD()-X"                  
## [11] "TimeGravityAccelerometerSTD()-Y"                  
## [12] "TimeGravityAccelerometerSTD()-Z"                  
## [13] "TimeBodyAccelerometerJerkMean()-X"                
## [14] "TimeBodyAccelerometerJerkMean()-Y"                
## [15] "TimeBodyAccelerometerJerkMean()-Z"                
## [16] "TimeBodyAccelerometerJerkSTD()-X"                 
## [17] "TimeBodyAccelerometerJerkSTD()-Y"                 
## [18] "TimeBodyAccelerometerJerkSTD()-Z"                 
## [19] "TimeBodyGyroscopeMean()-X"                        
## [20] "TimeBodyGyroscopeMean()-Y"                        
## [21] "TimeBodyGyroscopeMean()-Z"                        
## [22] "TimeBodyGyroscopeSTD()-X"                         
## [23] "TimeBodyGyroscopeSTD()-Y"                         
## [24] "TimeBodyGyroscopeSTD()-Z"                         
## [25] "TimeBodyGyroscopeJerkMean()-X"                    
## [26] "TimeBodyGyroscopeJerkMean()-Y"                    
## [27] "TimeBodyGyroscopeJerkMean()-Z"                    
## [28] "TimeBodyGyroscopeJerkSTD()-X"                     
## [29] "TimeBodyGyroscopeJerkSTD()-Y"                     
## [30] "TimeBodyGyroscopeJerkSTD()-Z"                     
## [31] "TimeBodyAccelerometerMagnitudeMean()"             
## [32] "TimeBodyAccelerometerMagnitudeSTD()"              
## [33] "TimeGravityAccelerometerMagnitudeMean()"          
## [34] "TimeGravityAccelerometerMagnitudeSTD()"           
## [35] "TimeBodyAccelerometerJerkMagnitudeMean()"         
## [36] "TimeBodyAccelerometerJerkMagnitudeSTD()"          
## [37] "TimeBodyGyroscopeMagnitudeMean()"                 
## [38] "TimeBodyGyroscopeMagnitudeSTD()"                  
## [39] "TimeBodyGyroscopeJerkMagnitudeMean()"             
## [40] "TimeBodyGyroscopeJerkMagnitudeSTD()"              
## [41] "FrequencyBodyAccelerometerMean()-X"               
## [42] "FrequencyBodyAccelerometerMean()-Y"               
## [43] "FrequencyBodyAccelerometerMean()-Z"               
## [44] "FrequencyBodyAccelerometerSTD()-X"                
## [45] "FrequencyBodyAccelerometerSTD()-Y"                
## [46] "FrequencyBodyAccelerometerSTD()-Z"                
## [47] "FrequencyBodyAccelerometerMeanFreq()-X"           
## [48] "FrequencyBodyAccelerometerMeanFreq()-Y"           
## [49] "FrequencyBodyAccelerometerMeanFreq()-Z"           
## [50] "FrequencyBodyAccelerometerJerkMean()-X"           
## [51] "FrequencyBodyAccelerometerJerkMean()-Y"           
## [52] "FrequencyBodyAccelerometerJerkMean()-Z"           
## [53] "FrequencyBodyAccelerometerJerkSTD()-X"            
## [54] "FrequencyBodyAccelerometerJerkSTD()-Y"            
## [55] "FrequencyBodyAccelerometerJerkSTD()-Z"            
## [56] "FrequencyBodyAccelerometerJerkMeanFreq()-X"       
## [57] "FrequencyBodyAccelerometerJerkMeanFreq()-Y"       
## [58] "FrequencyBodyAccelerometerJerkMeanFreq()-Z"       
## [59] "FrequencyBodyGyroscopeMean()-X"                   
## [60] "FrequencyBodyGyroscopeMean()-Y"                   
## [61] "FrequencyBodyGyroscopeMean()-Z"                   
## [62] "FrequencyBodyGyroscopeSTD()-X"                    
## [63] "FrequencyBodyGyroscopeSTD()-Y"                    
## [64] "FrequencyBodyGyroscopeSTD()-Z"                    
## [65] "FrequencyBodyGyroscopeMeanFreq()-X"               
## [66] "FrequencyBodyGyroscopeMeanFreq()-Y"               
## [67] "FrequencyBodyGyroscopeMeanFreq()-Z"               
## [68] "FrequencyBodyAccelerometerMagnitudeMean()"        
## [69] "FrequencyBodyAccelerometerMagnitudeSTD()"         
## [70] "FrequencyBodyAccelerometerMagnitudeMeanFreq()"    
## [71] "FrequencyBodyAccelerometerJerkMagnitudeMean()"    
## [72] "FrequencyBodyAccelerometerJerkMagnitudeSTD()"     
## [73] "FrequencyBodyAccelerometerJerkMagnitudeMeanFreq()"
## [74] "FrequencyBodyGyroscopeMagnitudeMean()"            
## [75] "FrequencyBodyGyroscopeMagnitudeSTD()"             
## [76] "FrequencyBodyGyroscopeMagnitudeMeanFreq()"        
## [77] "FrequencyBodyGyroscopeJerkMagnitudeMean()"        
## [78] "FrequencyBodyGyroscopeJerkMagnitudeSTD()"         
## [79] "FrequencyBodyGyroscopeJerkMagnitudeMeanFreq()"    
## [80] "Angle(TimeBodyAccelerometerMean,Gravity)"         
## [81] "Angle(TimeBodyAccelerometerJerkMean),GravityMean)"
## [82] "Angle(TimeBodyGyroscopeMean,GravityMean)"         
## [83] "Angle(TimeBodyGyroscopeJerkMean,GravityMean)"     
## [84] "Angle(X,GravityMean)"                             
## [85] "Angle(Y,GravityMean)"                             
## [86] "Angle(Z,GravityMean)"                             
## [87] "Activity"                                         
## [88] "Subject"

