



Predicting multiple targets of the mechanism of action responses of different drug samples
 







Team Members:
Tanakit Phamornratanakun
Priyanka Kare
Isabella Jaya Rani Chandrasekaran
Stephanie Brooks



Introduction : 
Previously, drugs generated using traditional procedures were put into clinical use without first understanding the biology underpinning the pharmacological activity. After a few decades, new technologies allowed drug research to take a much more specific model approach to the underlying biological mechanism of a disease, and this activity was given the name mechanism of action (MoA). Our group is using machine learning to identify insights or patterns between MoA and drug kinds that can help improve the drug development process.



Background :
Our project's goal is to use numerous feature engineering approaches on features before applying them to shallow machine learning models to obtain assessment metrics. Then figure out which feature or collection of features is the greatest, as well as which feature engineering technique is the best, and why. This can be done with the dataset we got.





















Model :

Architecture Diagram with explanation

The architecture of the project is kept simple. Firstly we have the acquisition of data which is taken from the kaggle with over 30 thousand rows.
Then we performed exploratory data analysis by checking for skewness and null values among others.
This data is then preprocessed further by the removal of irrelevant columns and labels.
This processed data is then passed through the various algorithms and model parameters with sparse techniques as tuning.
The obtained results are then further passed through the model tuning for better results.



Workflow diagram


Dataset

With over 30 thousand rows the train dataset and test dataset are split accordingly where the train dataset has 876 features with 23 thousand rows while the test set has around 4 thousand.

The features list contains:
The Sig_id which is a unique id for each of the drug’s signatures.
Feature g signifies the gene expression data.
Feature c signifies the cells viability data

There’s also the presence of control perturbation features like :
Cp_type which indicates samples treated with a compound (cp_vehicle) or with a control perturbation (ctrl_vehicle); control perturbations have no MoAs.
Cp_time that indicates treatment duration (24, 48, 72 hours)
Cp_dose which indicates treatment dose (high or low)

There’s a label list with over 207 one-hot encoding labels indicating the drug types


Detail design of Features with diagram

Analysis of data

Data Preprocessing
Out of 873 features 729 of them are moderately skewed or more that is why we need to apply log transformation. At the same time, we have to avoid the zero value problem before putting into the transformation by using a min-max scaler which also helps create a well-scaled numerical data range.

Figure 1.) data features skewness.

In this multilabel(multi output) class classification problem, there are numbers of feature that have strongly imbalance class, only 0.3417%  of target label values are not zero


Figure 2.) countplot of number of multilabel

According to figure2, the target labels of this dataset are strongly sparse, also we found out that some of the target labels contain less than 6 records of class 1(out of 23814
records) . In order to fix this problem, we decided to drop all the target labels that strongly imbalance target labels, otherwise it will lead to more problems after we split the dataset into train and test sets if one of them contains only one class. Upsampling could be used to solve this problem but the available packages are not compatible with multilabel class data at the moment. 


Implementation

Algorithms / Pseudocode

Logistic Regression









Decision Tree Classifier













Random Forest Classifier

K-Nearest Neighbor Classifier

	



Explanation of implementation
Acquired data from Kaggle Competition
Checked for null, unique values, its correctness and skewness 
Removed unnecessary columns, sparse label and encode categorical data
Split train and test datasets with 7:3 ratio
Unskewed data using log transformation
Create variation of parameters for the models
Upsampling data using SMOTE that have small numbers of target labels (by 200, 500, 1000 samples)
Using principal Components Analysis(components = 15,30,50) in order to reduce dimension of features.
Applying 4 shallow learning algorithms that support multilabel classification data which are Logistic Regression(with chain classifier), Decision TreeClassification, Random Forest Classification and KNN Classification
Using GridSearch CrossValidation technique with cv = 5 in order to find the best model.
Get results, evaluate result and redo model tuning






Results


Algorithms / Number of up-sample
0
200
500
1000
 
Logistic Regression
0.314790997
0.258198026
0.23627094
0.217536642
Decision Tree Classifier
0.230899256
0.216373325
0.190770135
0.17377772
Random Forest Classifier
0.202934418
0.18358785
0.170419963
0.154259608
K-Nearest Neighbor Classifier
 
0.279634248
0.26758794
0.257772753
0.269776389


Table 1) Showing model performance(micro f1 score) according to different algorithms and number of up-samples




Project Management

Work completed: 
From the given dataset which contains over 2500 columns we have performed EDA, we have checked the column data types, its values, null values, incorrect imputation, unique values, negative values, and skewness. After this splitting of data is done where we split the data into a train and test set. We took 30 % of data as the test data and the remaining 70% is considered as the training dataset.
In conclusion, among the different algorithms, Logistic Regression performs the best with limited performance. The assumption for this performance is there are too many classes (sparse data) for the target labels. In order to solve this problem, our group applied the SMOTE up-sampling technique which resulted in lower micro f1-score because models couldn’t avoid highly biased target classes.






Responsibility (Task,Person)
TASK1: Exploratory Data Analysis- Isabella, Priyanka
 
TASK2: Feature Extraction and Analysis- Tanakit, Stephanie, Priyanka 
 
TASK3: Model training- Tanakit, Stephanie, Isabella

TASK4: Parameter Tuning and work around - Tanakit, Stephanie

TAsk 5: Making report and presentation: Stephanie, Isabella, Priyanka

Contributions (members/percentage)
Tanakit Phamornratanakun- 25% (worked on the data preprocessing methods, Model training and parameter tuning)
Priyanka Kare- 25% (worked on Exploratory Data Analysis, Feature Extraction and Analysis, making documents and slides)
Isabella Jaya Rani Chandrasekaran- 25% (worked on Exploratory Data Analysis and to prepare the data to extract right features, making documents and slides)
Stephanie Brooks- 25% (worked on analysis of the data and to determine the right features and the model to be used, Presentation Video of codes and slides)


Issues/Concerns
Having a strongly imbalanced class leads to wrong metrics evaluation, models could not calculate the score accurately because sometimes test or validate datasets contain only one class. 
Multilabel classification problem has a limited number of support libraries, algorithms and metrics.
The constraints for this project are 
1. Running the models needs a significant amount of resources 
2. Limited numbers of algorithms 
3. Limited evaluation metrics for given algorithms.



References/Bibliography :

The Connectivity Map (September, 2020). Mechanisms of Action (MoA) Prediction from https://www.kaggle.com/c/lish-moa/data


Aravind Subramanian,Rajiv Narayan,Steven M. Corsello. A Next Generation Connectivity Map: L1000 Platform and the First 1,000,000 Profiles. Cell, Elsevier, (2017). https://doi.org/10.1016/j.cell.2017.10.049
https://www.cell.com/cell/fulltext/S0092-8674(17)31309-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS0092867417313090%3Fshowall%3Dtrue

Corsello, S.M., Nagari, R.T., Spangler, R.D. et al. Discovering the anticancer potential of non-oncology drugs by systematic viability profiling. Nat Cancer 1, 235–248 (2020). https://doi.org/10.1038/s43018-019-0018-6
https://www.nature.com/articles/s43018-019-0018-6#citeas

Si, W., Shen, J., Zheng, H. et al. The role and mechanisms of action of microRNAs in cancer drug resistance. Clin Epigenet 11, 25 (2019). https://doi.org/10.1186/s13148-018-0587-8
https://clinicalepigeneticsjournal.biomedcentral.com/articles/10.1186/s13148-018-0587-8

Schenone, M., Dančík, V., Wagner, B. et al. Target identification and mechanism of action in chemical biology and drug discovery. Nat Chem Biol 9, 232–240 (2013). https://doi.org/10.1038/nchembio.1199
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5543995/


Videos

Code Runthrough
https://drive.google.com/file/d/1qmSggPXSWkEUDDzc1JzAiUcPQlWh2WxN/view?usp=sharing

Presentation Runthrough

Part1: https://unt.zoom.us/rec/share/h0lUHmTd0SIKhz_x3ZXdJgpSkkTHG_SkPuHc7wFVO5TvH4-VMsmnzYJOLpu0g9UA.3trS7-ZK1aK_7vzC?startTime=1638504351000

Part2:
https://unt.zoom.us/rec/share/h0lUHmTd0SIKhz_x3ZXdJgpSkkTHG_SkPuHc7wFVO5TvH4-VMsmnzYJOLpu0g9UA.3trS7-ZK1aK_7vzC?startTime=1638507266000


GitHub
https://github.com/TanakitPhamorn/MoA-Prediction

Presentation
https://docs.google.com/presentation/d/1p-8jYzFBSw_Lp5Ezm4aEF-NrWb90ckl--w-koC8kVmM/edit?usp=sharing


