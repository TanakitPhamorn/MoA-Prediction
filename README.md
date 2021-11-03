# MoA-Prediction
Predicting multiple targets of the mechanism of action responses of different drug samples
 
Team Members:
·        Tanakit Phamornratanakun
·        Priyanka Kare
·        Isabella Jaya Rani Chandrasekaran
·        Stephanie Brooks
 
Idea Description:
The idea of our project is that we can apply multiple feature engineering techniques on the features before applying it to shallow machine learning models in order to get evaluation metrics. Then find the best feature or set of features and the best feature engineering technique and the reasons behind it. This can be performed on the dataset we obtained via Kaggle which has 876 features in integer and decimal format with multilabel class.


Goals and Objectives:
The goal is to predict the multilabel class of type of drugs given a significantly high number of Mechanisms of Actions features at hand.
Objectives
Identify and visualize the best  feature engineering techniques which  provide the best outcome 
Identify the best feature or set of features in this dataset.
Finding the best shallow machine learning techniques among Gradient, boosting Classifier, Naïve Bayes Classifier and Linear Support Vector Classifier
 
Motivation:
In the past, medicines developed via the traditional methods were put into immediate clinical use before the mechanism behind the biology for the pharmacological activities were understood. After a few decades with the new technologies drug discovery made a far more targeted model approach towards the underlying biological mechanism of a disease, this activity was assigned a label known as mechanism of action or MoA. Using machine learning,  our group aim to find insights or patterns between MoA and drug types which can improving the further development process of drugs 

Significance:
The achievement of this project can lead to improvement of drug developments, simplify the process of drug research, testing and creations not only for pharmaceutical companies but also for the whole world.

Literature Survey:
A connectivity map that shows the results of treating cells with different drugs that assists in mechanism of action discovery.
Aravind Subramanian,Rajiv Narayan,Steven M. Corsello. A Next Generation Connectivity Map: L1000 Platform and the First 1,000,000 Profiles. Cell, Elsevier, (2017). https://doi.org/10.1016/j.cell.2017.10.049
A paper that explores the screening of non-oncology drugs for cancer treatments.
Corsello, S.M., Nagari, R.T., Spangler, R.D. et al. Discovering the anticancer potential of non-oncology drugs by systematic viability profiling. Nat Cancer 1, 235–248 (2020). https://doi.org/10.1038/s43018-019-0018-6
A holistic understanding of the functions of miRNAs in drug resistance will help us develop better strategies to regulate them efficiently.
Si, W., Shen, J., Zheng, H. et al. The role and mechanisms of action of microRNAs in cancer drug resistance. Clin Epigenet 11, 25 (2019). https://doi.org/10.1186/s13148-018-0587-8
Computational inference methods and target identification via the biochemical interactions. 
Schenone, M., Dančík, V., Wagner, B. et al. Target identification and mechanism of action in chemical biology and drug discovery. Nat Chem Biol 9, 232–240 (2013). https://doi.org/10.1038/nchembio.1199

Features:
The train dataset(with labels) has 876 features and 23814 rows with 
The test dataset(without labels) has 876 features and 3982 rows Features List
Sig_id: the unique ID for each drugs’ signatures.
Features g- : signify gene expression data
Features c- : signify cell viability data. 
Cp_type indicates samples treated with a compound (cp_vehicle) or with a control perturbation (ctrl_vehicle); control perturbations have no MoAs.
Cp_time indicate treatment duration (24, 48, 72 hours)
Cp_dose indicate treatment dose (high or low)
Label List:
207 one-hot encoding labels indicate drug types


Expected Outcome:
Behavioral and pattern predictions of the drugs and MOA would save significant time in drug development. Different combinations of drugs could yield more efficient or entirely new possible combinations for treatment. A patient’s long and short term viability will also be improved if we are able to determine drug(s) behaviour and effectiveness. All of which result in a company’s capital gains for time saved during testing. The ability to diversify treatment options by expanding a drug’s treatment classification will also result in increased capital.







References:
The Connectivity Map (September, 2020). Mechanisms of Action (MoA) Prediction from https://www.kaggle.com/c/lish-moa/data


Aravind Subramanian,Rajiv Narayan,Steven M. Corsello. A Next Generation Connectivity Map: L1000 Platform and the First 1,000,000 Profiles. Cell, Elsevier, (2017). https://doi.org/10.1016/j.cell.2017.10.049
https://www.cell.com/cell/fulltext/S0092-8674(17)31309-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS0092867417313090%3Fshowall%3Dtrue

Corsello, S.M., Nagari, R.T., Spangler, R.D. et al. Discovering the anticancer potential of non-oncology drugs by systematic viability profiling. Nat Cancer 1, 235–248 (2020). https://doi.org/10.1038/s43018-019-0018-6
https://www.nature.com/articles/s43018-019-0018-6#citeas

Si, W., Shen, J., Zheng, H. et al. The role and mechanisms of action of microRNAs in cancer drug resistance. Clin Epigenet 11, 25 (2019). https://doi.org/10.1186/s13148-018-0587-8
https://clinicalepigeneticsjournal.biomedcentral.com/articles/10.1186/s13148-018-0587-8

Schenone, M., Dančík, V., Wagner, B. et al. Target identification and mechanism of action in chemical biology and drug discovery. Nat Chem Biol 9, 232–240 (2013). https://doi.org/10.1038/nchembio.1199
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5543995/
