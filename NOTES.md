## considerations

### EDA
- goal: look at the data. any data that we use for the model should be filled
- if its 60% full you keep the column
- filtering the data (Forsome columns, the vast majority missing, you drop them. filter 40 columns).
- how you will impute the data (median or main)
- use sklearn's `LabelEncoder` (eg. apple/android = 0/1)
- 400 features left. Either do full feature or feature selection. (`mutual_info_classification`)
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

[encoding text to numeric data](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html
)

[area-under-the-curve score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html
)

reduce dimension/features
- [feature selection](https://scikit-learn.org/stable/modules/feature_selection.html)
- [mutual info classification](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.mutual_info_classif.html)

after all table permutes/removal, [save to a new file (for quicker re-use)](https://www.geeksforgeeks.org/pandas/saving-a-pandas-dataframe-as-a-csv/
)