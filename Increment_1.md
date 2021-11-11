Predicting multiple targets of the mechanism of action responses of different drug samples

Project Title and Team Members 

Tanakit Phamornratanakun
Priyanka Kare
Isabella Jaya Rani Chandrasekaran
Stephanie Brooks

Goals and Objectives:

Motivation : 
Previously, drugs generated using traditional procedures were put into clinical use without first understanding the biology underpinning the pharmacological activity. After a few decades, new technologies allowed drug research to take a much more specific model approach to the underlying biological mechanism of a disease, and this activity was given the name mechanism of action (MoA). Our group is using machine learning to identify insights or patterns between MoA and drug kinds that can help improve the drug development process.

Significance :
The successful completion of this project will boost medication development by simplifying the process of drug research, testing, and creation not only for pharmaceutical corporations but for the entire world.

Objectives :
Determine and illustrate the most effective feature engineering strategies for achieving the greatest results.
Determine which feature or group of characteristics in this dataset is the best like Gradient, boosting Classifier, Naive Bayes Classifier, and Linear Support Vector Classifier were chosen as the top shallow machine learning algorithms.





Features 
The train dataset comprises 876 features and 23814 rows with labels.
The test dataset comprises 876 features and 3982 rows (without labels).
Sig id: a unique identifier for each drug's signature.
Features g-: denotes data on gene expression.
Features c- denotes cell viability information.
Cp type denotes whether the samples were treated with a compound (cp vehicle) or a control perturbation (ctrl vehicle); control perturbations do not have MoAs.
The treatment period is indicated by Cp time (24, 48, 72 hours)
The treatment dose is indicated by Cp dose (high or low)
207 one-hot encoding labels are used to designate medication kinds.

Related Work 
A connectivity map that shows the results of treating cells with different drugs that assists in mechanism of action discovery.
Aravind Subramanian,Rajiv Narayan,Steven M. Corsello. A Next Generation Connectivity Map: L1000 Platform and the First 1,000,000 Profiles. Cell, Elsevier, (2017). https://doi.org/10.1016/j.cell.2017.10.049

A paper that explores the screening of non-oncology drugs for cancer treatments.
Corsello, S.M., Nagari, R.T., Spangler, R.D. et al. Discovering the anticancer potential of non-oncology drugs by systematic viability profiling. Nat Cancer 1, 235–248 (2020). https://doi.org/10.1038/s43018-019-0018-6

A holistic understanding of the functions of miRNAs in drug resistance will help us develop better strategies to regulate them efficiently.
Si, W., Shen, J., Zheng, H. et al. The role and mechanisms of action of microRNAs in cancer drug resistance. Clin Epigenet 11, 25 (2019). https://doi.org/10.1186/s13148-018-0587-8

Computational inference methods and target identification via the biochemical interactions.
Schenone, M., Dančík, V., Wagner, B. et al. Target identification and mechanism of action in chemical biology and drug discovery. Nat Chem Biol 9, 232–240 (2013). https://doi.org/10.1038/nchembio.1199


Dataset 
	The Dataset contains overall 6 .csv files, with over 2500 columns, they are :
sample_submission.csv
test_features.csv
train_drug.csv
train_features.csv
train_targets_nonscored.csv
train_targets_scored.csv

Detail design of Features
Encode the categorical features: 'cp_type', 'cp_time', 'cp_dose'
Rescale numerical features using min-max scaler
Unskew numerical features that have skew bias <-0.5 and > 0.5 by using log transformation
Drop sparse target features (features that have the fewer class equal or less than 6 records)
Principal component analysis between [5,15,30,60,90,120] numbers of features
SMOTE upsampling [100,200,1000,2000] numbers of upsampling 

Analysis
Out of 873 features 729 of them are moderately skewed or more that is why we need to apply log transformation. At the same time, we have to avoid the zero value problem before putting into the transformation by using a min-max scaler which also helps create a well-scaled numerical data range.

Figure 1.) data features skewness.
In this multilabel(multi output) class classification problem, there are numbers of feature that have strongly imbalance class, only 0.3417%  of target label values are not zero

Figure 2.) countplot of number of multilabel

According to figure2, the target labels of this dataset are strongly sparse, also we found out that some of the target labels contain less than 6 records of class 1(out of 23814
records) . In order to fix this problem, we decided to drop all the target labels that strongly imbalance target labels, otherwise it will lead to more problems after we split the dataset into train and test sets if one of them contains only one class. Upsampling could be used to solve this problem but the available packages are not compatible with multilabel class data at the moment. 

Implementation
Feature engineering techniques
Label Encoder
Min-Max Scaler
Log Transformation
Principal component analysis
SMOTE upsampling
Model Algorithms
Applied every algorithm using Grid Search Cross Validation Technique
Logistic Regression
DecisionTreeClassifier
RandomForestClassifer

Metrices
Compute Area Under the Receiver Operating Characteristic Curve (ROC AUC) One-vs-rest
F1 Micro( Calculate metrics globally by considering each element of the label indicator matrix as a label)
Multilabel Confusion Matrix
Preliminary Results
Logistic Regression
Best Parameters
{'clf__classifier__C': 21.54434690031882, 'pca__n_components': 30}
Best f1(micro) score
0.2843991451586388
Confusion Matrix(label index = 58)


Project Management

Implementation status report

Work completed:

Description
From the given dataset which contains over 2500 columns we have performed EDA, we have checked the column data types, its values, null values, incorrect imputation, unique values, negative values, and skewness. After this splitting of data is done where we split the data into a train and test set. We took 30 % of data as the test data and the remaining 70% is considered as the training dataset.
Now we have created the first model without up sampling, here logistic regression has been used and we have used Grid search cross validation to find the best hyperparameter and then the accuracy is determined.

Responsibility
TASK1: Exploratory Data Analysis- Isabella, Priyanka
 
TASK2: Feature Extraction and Analysis- Tanakit, Stephanie, Priyanka 
 
TASK3: Model training- Tanakit, Stephanie, Isabella

Contributions (members/percentage)
Tanakit Phamornratanakun- 40% (worked on the data preprocessing methods, Model training and parameter tuning)
Priyanka Kare- 20% (worked on Exploratory Data Analysis, Feature Extraction and Analysis)
Isabella Jaya Rani Chandrasekaran- 20% (worked on Exploratory Data Analysis and to prepare the data to extract right features)
Stephanie Brooks- 20% (worked on analysis of the data and to determine the right features and the model to be used)


Work to be completed

Description
Further we are planning to improve the accuracy by using other models like DecisionTree classifier and RandomForest classifier. The main enhancement which we will perform is to use SMOTE upsampling for the next models which we use.

Responsibility (Task, Person)
Implementation of SMOTE- Tanakit Phamornratanakun, Isabella
DecisionTree classifier- Priyanka Kare
RandomForest classifier- Stephanie Brooks



Issues/Concerns
Having a strongly imbalanced class leads to wrong metrics evaluation, models could not calculate the score accurately because sometimes test or validate datasets contain only one class. 
Multilabel classification problem has a limited number of support libraries, algorithms and metrics.

References/Bibliography

The Connectivity Map (September, 2020). Mechanisms of Action (MoA) Prediction from https://www.kaggle.com/c/lish-moa/data


Aravind Subramanian,Rajiv Narayan,Steven M. Corsello. A Next Generation Connectivity Map: L1000 Platform and the First 1,000,000 Profiles. Cell, Elsevier, (2017). https://doi.org/10.1016/j.cell.2017.10.049
https://www.cell.com/cell/fulltext/S0092-8674(17)31309-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS0092867417313090%3Fshowall%3Dtrue

Corsello, S.M., Nagari, R.T., Spangler, R.D. et al. Discovering the anticancer potential of non-oncology drugs by systematic viability profiling. Nat Cancer 1, 235–248 (2020). https://doi.org/10.1038/s43018-019-0018-6
https://www.nature.com/articles/s43018-019-0018-6#citeas
Si, W., Shen, J., Zheng, H. et al. The role and mechanisms of action of microRNAs in cancer drug resistance. Clin Epigenet 11, 25 (2019). https://doi.org/10.1186/s13148-018-0587-8
https://clinicalepigeneticsjournal.biomedcentral.com/articles/10.1186/s13148-018-0587-8

Schenone, M., Dančík, V., Wagner, B. et al. Target identification and mechanism of action in chemical biology and drug discovery. Nat Chem Biol 9, 232–240 (2013). https://doi.org/10.1038/nchembio.1199
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5543995/
https://scikit-learn.org/stable/modules/model_evaluation.html
https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html
https://scikit-learn.org/stable/modules/multiclass.html
https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html
https://scikit-learn.org/stable/modules/generated/sklearn.multioutput.ClassifierChain.html#sklearn.multioutput.ClassifierChain
https://scikit-learn.org/stable/modules/compose.html
https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html


Links :
https://github.com/TanakitPhamorn/MoA-Prediction.git
https://drive.google.com/file/d/18psKIKIy-Gcu86r3LJzy5wv-eO_Ho46p/view?usp=sharing

