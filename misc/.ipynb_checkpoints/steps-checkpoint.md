### TODO:
- choose sentiment analysis method
- non-english reviews -- can the chosen sentiment analysis engine handle them?
### preprocessing
- `dropna()` to remove 174 rows with missing year (tiny subset)
- parse 2 columns boolean columns `'is_early_access'` and `'received_free'` from front of `'user_review'`
- add boolean column `'is_ascii_art'` to detect ascii art columns

### processing
- feature reduction using one of methods from lab 6: 
  - might as well use `sklearn.feature_selection.SelectKBest`, since data is labelled? (supervised)
  - others: 
    - `RFE` (recursive feature elimination) (unsupervised): `from sklearn.linear_model import Perceptron`
    - `PCA` (principal component analysis) (unsupervised): `from sklearn.decomposition import PCA1`
    
- use a library to do sentiment analysis on `'user_review'`, add these as as columns to the dataframe as input to the classifier
- SVM or logistic classifier?
- evaluate based on number
### other notes

| method | parametric? | normalize input? | supervised/unsupervised | other notes |
---------------------------------------------------------------------------------------
| SVM | | yes | supervised | handles high dimensional data well, not noise |
| Decision Tree | | no, i think? | supervised | |
| k Nearest Neighbors | yes, doesn't make assumption on data | yes | supervised |   |
K-Means | | | unsupervised | `TODO` |

`classification report` from lab 5: precision    recall  f1-score   support
