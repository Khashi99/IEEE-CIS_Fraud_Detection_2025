## considerations

### EDA
- goal: look at the data. any data that we use for the model should be filled
- if its 60% full you keep the column
- filtering the data 
    - for some columns, the vast majority missing, you drop them. filter 40 columns.
- how you will impute the data (median or main)
- use sklearn's `LabelEncoder` (eg. apple/android = 0/1)
- 400 features left. 
    - either do full feature or feature selection. (`mutual_info_classification`)
- merge relevent columns (card1-card6)

### models
- don't need to do PCA (just do feature selection-from sklearn (not the feature extraction?))
- sampling is faster (for SVM-it will take long!). 
- improve accuracy with `xgboost`
- do logistic regression (because it's faster) , then SVM and then decision trees. 
- if you want to do hyperparam tuning, you can create a [sklearn Pipeline](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html)
- for some algorithms, you can use n_jobs (logistic regression)
    - put -1 to get the most!
- No DBSCAN for the project. we are just doing binary classification (fraud or not).

### submission    
- The score that you use is the area under the curve (ROC)!
    - 95% of existing transactions in the dataset are not fraud
- submit a `csv` that has the probabilities (not zeros and ones)

## references
- [preprocessing data](https://scikit-learn.org/stable/modules/preprocessing.html#preprocessing)
- [imputation of missing values](https://scikit-learn.org/stable/modules/impute.html)
- [encoding text to numeric data](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)
- [StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html)
    - used by all models
- [Support Vector Machines](https://scikit-learn.org/stable/modules/svm.html#svm)
- [Decision Trees](https://scikit-learn.org/stable/modules/tree.html)
- [xgboost docs](https://xgboost.readthedocs.io/en/latest/index.html)
    - [xgboost with scikit-learn interface](https://xgboost.readthedocs.io/en/latest/python/python_intro.html#scikit-learn-interface)
- [area-under-the-curve score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)

reduce dimension/features
- [feature selection](https://scikit-learn.org/stable/modules/feature_selection.html)
- [mutual info classification](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.mutual_info_classif.html)

after all table permutes/removal, [save to a new file (for quicker re-use)](https://www.geeksforgeeks.org/pandas/saving-a-pandas-dataframe-as-a-csv/)

### example code
- [EDA explore data](https://www.kaggle.com/code/artgor/eda-and-models#Data-Exploration)
- [EDA feature-analysis and xgboost](https://www.kaggle.com/code/graykun/ieee-cis-fraud-detection-submission/notebook)
- [EDA in-depth](https://www.kaggle.com/code/suoires1/fraud-detection-eda-and-modeling)
- [SVM, DT, XGBOOST](https://www.kaggle.com/code/mikestvictor/msv-fraud-detection/notebook)
- [models compare](https://www.kaggle.com/code/vchulski/ieee-simple-models-comparison)