### TODO:
<!-- - choose sentiment analysis method -->
<!-- - non-english reviews -- can the chosen sentiment analysis engine handle them? -->
### preprocessing
- `dropna()` to remove 174 rows with missing year (tiny subset)
- parse 2 columns boolean columns `'is_early_access'` and `'received_free'` from front of `'user_review'`
- explicitly detect ascii art reviews. instead of removing these, add new boolean column `'is_ascii_art'`.

### processing
- feature reduction using one of methods from lab 6: 
  - might as well use `sklearn.feature_selection.SelectKBest`, since data is labelled? (supervised)
  - others: 
    - `RFE` (recursive feature elimination) (unsupervised): `from sklearn.linear_model import Perceptron`
    - `PCA` (principal component analysis) (unsupervised): `from sklearn.decomposition import PCA1`
#### 1. sentiment analysis
I will use a pre-trained sentiment analysis model to rate the sentiment of the reviews. This model was trained on Twitter tweets, so hopefully it will  be able to detect sarcasm and handle internet-speak when determining positive vs. negative sentiment. Store the sentiment value in a new column called `sentiment`. This will replace the actual `user_review` as input to the classifier.
#### 2. classifier:
1. do univariate feature selection with `sklearn.feature_selection.SelKBest`
2. run through a SVM classifier.
#### parameters:
`sklearn.feature_selection.SelKBest`: `k`, `score_func: chi2, f_classif, r_regression`
SVM: `gamma`, `C`


    
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
