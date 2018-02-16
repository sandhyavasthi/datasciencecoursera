# datasciencecoursera
# peer graded assignment week 4 getting and cleaning data
#this R script called run_analysis.R that does the following.

#Merges the training and the test sets to create one data set.
#Extracts only the measurements on the mean and standard deviation for each measurement.
#Uses descriptive activity names to name the activities in the data set
#Appropriately labels the data set with descriptive variable names.
#From the data set in step 4, creates a second, independent tidy data set with the
#average of each variable for each activity and each subject.
# data for this is taken from UCI HAR dataset

# to do this you need data.table and reshap2 package

require("reshape2")
require("data.table")

# reading labels in data
activity_labels <- read.table("./UCI HAR Dataset/activity_labels.txt")[,2]

# reading features in data table
features <- read.table("./UCI HAR Dataset/features.txt")[,2]

# measurements on the mean and standard deviation for each measurement
extract_features <- grepl("mean|std", features)


#  loading test set and test labels 

X_set<-read.table("./UCI HAR Dataset/test/X_test.txt")
y_set<-read.table("./UCI HAR Dataset/test/y_test.txt")
subject_test<-read.table("./UCI HAR Dataset/test/subject_test.txt")

names(X_set) = features

# Extract only the measurements on the mean and standard deviation for each measurement.
X_set = X_set[,extract_features]

# Load activity labels
y_set[,2] = activity_labels[y_set[,1]]
names(y_set) = c("Activity_ID", "Activity_Label")
names(subject_test) = "subject"

# Bind data
test_data <- cbind(as.data.table(subject_test), y_set, X_set)

# Load and process training set & training labels data.
X_train <- read.table("./UCI HAR Dataset/train/X_train.txt")
y_train <- read.table("./UCI HAR Dataset/train/y_train.txt")

subject_train <- read.table("./UCI HAR Dataset/train/subject_train.txt")

names(X_train) = features

# Extract only the measurements on the mean and standard deviation for each measurement.
X_train = X_train[,extract_features]

# Load activity data
y_train[,2] = activity_labels[y_train[,1]]
names(y_train) = c("Activity_ID", "Activity_Label")
names(subject_train) = "subject"

# Bind data
train_data <- cbind(as.data.table(subject_train), y_train, X_train)

# Merging test data and training  data
data = rbind(test_data, train_data)

id_labels = c("subject", "Activity_ID", "Activity_Label")
data_labels = setdiff(colnames(data), id_labels)
melt_data=melt(data, id = id_labels, measure.vars = data_labels)

# Apply mean function to dataset using dcast function
tidy_data<-dcast(melt_data, subject + Activity_Label ~ variable, mean)

write.table(tidy_data, file = "./tidy_data.txt")
