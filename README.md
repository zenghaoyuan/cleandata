#　 explanation about run_analysis.R
  First,read related data into R. I use directory to denote where you store the downloaded and unzipped file.
  
  You should use a text editor to grasp a general idea of what the data look like combined with feature.txt which tells you what variable the specific number corresponds to. If you understand the data correctly,then you should know how to merge them.
  
  Before merging them,the default colnames are something like "V1" "V2".If you merge something without renaming, it would cause some error like duplicated colnames in further steps.So it is bettern that you name some data to tell one from another.
  
  Next in my function, we get rawdata.We have denoted the first two columns as subject and activity respectively.For convenience,we can rename other columns as well.So I extract the information in feature.txt and use it to rename the rawdata.

  Our assignment asks us to extracts only the measurements on the mean and standard deviation for each measurement. So I use grep function to get the index of the columns I need.Don't miss the first two columns and use order function to preserve the order.Then I use the index to get the wanted data called betterdata.
  
  Then we need to use descriptive activity names to name the activities in the data set. So  I creat a factor data.frame called activity.Note in betterdata,we use number to denote activity like 5 stands for STANDING.So when creating this data.frame, make sure the mapping is right.After that,you can use the dataframe to map the second column of betterdata into the activity name.(Character is more convient,so I convert the factor variable into character)
  
  Finally we come to last step.Because the first two columns are not numeric,so we may want to put it aside for convience.That is what puredata and finaldata do. We want to creates a second independent tidy data set with the average of each variable for each activity and each subject.I just copy the puredata to store the mean value I get.Because we have 30 subjects and 6 activitis,then we have 180 observations, which means I only need the first 180 rows of meandata.Remember what the first row of meandata mean.At last,I will combine the meandata with finaldata which indicates they are consistant.Precisely, the first row of meandata is the observation of subject 1 doing activity 1.Mathematically,the observation of subject i doing activity j should be in the (i-1)*6+j row. 
  
  As for “ meandata[6*(i-1)+j,]<-colMeans(puredata[rawdata[,1]==i&rawdata[,2]==j,])”, we calculate the meanvalue.(in rawdata,we use number to denote activity,so it is more easy to index.)
  
  Combining the meandata with finaldata get the result.
  
  
