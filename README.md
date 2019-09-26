# NYC-HS-Success

This project attempts to classify “successful” NYC public high schools, using a rich array of school quality data provided by the DOE.  I attempt to predict target classifications based on a high school being above (successful) or below (not successful) the mean NYC HS graduation rate.

## Tech Stack
- Python
- Pandas
- Matplotlib
- Seaborn
- Scikit-Learn

## EDA
For modeling I use feature and target data from NYC high schools for graduation years 2015, 2016, and 2017.  Data was cleaned, analyzed, and categorical data was label-encoded.

There was a fairly even distribution of “successful” and non-successful high schools given graduation rates.

![](/plots/target_dist.png)

![](/plots/class_count.png)

## Modeling

### Baseline

As baseline "dummy" model yielded the following results:


==================================================

STRATIFIED DUMMY CLASSIFIER


Accuracy is: 51.02040816326531

AUC is: 0.52
--------------------------------------------------
Confusion Matrix
col_0     0    1  All
target               
0        65   47  112
1        73   60  133
All     138  107  245
--------------------------------------------------
              precision    recall  f1-score   support

           0       0.47      0.58      0.52       112
           1       0.56      0.45      0.50       133

    accuracy                           0.51       245
   macro avg       0.52      0.52      0.51       245
weighted avg       0.52      0.51      0.51       245


### Decision Tree

Decision Tree yielded fairly good results, and of course it is an interpretable model - we can see which features drive the bulk of its classification prediction (below).

#### Score/Accuracy

==================================================

DECISION TREE


Accuracy is: 83.26530612244898

AUC is: 0.83
--------------------------------------------------
Confusion Matrix
col_0     0    1  All
target               
0        90   22  112
1        19  114  133
All     109  136  245
--------------------------------------------------
              precision    recall  f1-score   support

           0       0.83      0.80      0.81       112
           1       0.84      0.86      0.85       133

    accuracy                           0.83       245
   macro avg       0.83      0.83      0.83       245
weighted avg       0.83      0.83      0.83       245

#### Feature Selection
![](/plots/tree_features.png)

### Random Forest

Random Forest improved the classification prediction results, while also preserving interpretability.

#### Score/Accuracy

==================================================

DEFAULT RANDOM FOREST


Accuracy is: 84.89795918367346

AUC is: 0.85
--------------------------------------------------
Confusion Matrix
col_0     0    1  All
target               
0        97   15  112
1        22  111  133
All     119  126  245
--------------------------------------------------
              precision    recall  f1-score   support

           0       0.82      0.87      0.84       112
           1       0.88      0.83      0.86       133

    accuracy                           0.85       245
   macro avg       0.85      0.85      0.85       245
weighted avg       0.85      0.85      0.85       245


#### Feature Selection
![](/plots/forest.png)


Other models, such as XG Boost and SVM, did not yield as good results.

## Conclusion

Not surprisingly, core metrics of educational performance, including “Average Grade 8 English Proficiency”, and “Average Grade 8 Math Proficiency” were among the main drivers of a school’s success!

## Next Steps
- The feature engineering and modeling exercises were fairly coarse; 
- Engineering new features, or tuning the models differently, may yield less obvious insights.
