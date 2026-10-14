# Health Data Modelling – Labs

Practical assignments of the Master's course on health data modelling (M2). The three labs use scikit-learn in Jupyter notebooks, with results and written answers in each notebook (`.ipynb`) and in a ready-to-read HTML export (`.html`).

**Author:** Gloria Badohoun

## Repository structure

```
health-data-labs/
├── lab1/   Decision trees on obesity data
├── lab2/   Text representation and ensemble classifiers
└── lab3/   Linear models vs ensembles on medical abstracts
```

## Lab 1 – Decision trees on obesity data

- **Data:** `obesity_data.csv` (1,000 individuals, 7 variables) and `obesity_binary.csv` (8 individuals, binary attributes).
- **Content:** data description, preparation, CART decision trees with Gini and entropy criteria, then ID3 and C4.5 (gain ratio) implemented from scratch.
- **Key points:**
  - `BMI` was removed from the features because it is computed from height and weight and directly defines the target categories (data leakage).
  - Test accuracy: 91.5% (Gini) and 94.5% (entropy); both trees overfit (100% training accuracy).
  - On the small binary dataset, ID3 and C4.5 give the same tree (root on `Weight`, depth 1, 2 leaves).
- **Files:** `lab1/lab1.ipynb`, `lab1/lab1.html`, the two CSV files.

## Lab 2 – Text representation and ensemble classifiers

- **Data:** mental-health statements (7 classes, about 51,000 texts) and the Medical Abstracts corpus (5 classes, 11,550 training and 2,888 test abstracts). The datasets are **not included** (see below).
- **Content:** stop-word removal, Bag of Words and TF-IDF (manual implementation and scikit-learn), comparison with a decision tree, then Decision Tree, Bagging, Random Forest, AdaBoost, Gradient Boosting and Stacking on medical abstracts, with training times.
- **Key points:**
  - BoW and TF-IDF are practically equivalent for a decision tree (macro F1 0.538 vs 0.529).
  - Best model on the medical abstracts: Gradient Boosting (accuracy 0.550, macro F1 0.528).
- **Files:** `lab2/Lab2_Health_Data_Modelling.ipynb`, `lab2/Lab2_Health_Data_Modelling.html`.

## Lab 3 – Linear models vs ensembles on medical abstracts

- **Data:** Medical Abstracts corpus (same as Lab 2, not included).
- **Content:** TF-IDF representation, binary task (neoplastic vs non-neoplastic) with Logistic Regression (probabilities, odds, influential words) and SVM; then the 5 original classes, class imbalance analysis and class weighting; finally a comparison of 8 classifiers with training times.
- **Key points:**
  - Binary task: Logistic Regression slightly better than the linear SVM (F1 0.660 vs 0.645, ROC-AUC 0.916 vs 0.890).
  - Class weighting improves the multinomial Logistic Regression (macro F1 0.564 to 0.601) and barely helps the SVM.
  - Best model on 5 classes: Stacking (accuracy 0.633, macro F1 0.628), but also the slowest (230 s); Logistic Regression is the best speed/performance compromise (accuracy 0.573, 10.8 s).
- **Files:** `lab3/Lab3_Health_Data_Modelling.ipynb`, `lab3/Lab3_Health_Data_Modelling.html`.

## Datasets for Labs 2 and 3

The large datasets are not stored in this repository. Download them from
<https://github.com/EDJINEDJA/Health-Data-modelling> (folder `lab2`) and place them as follows:

```
lab2/data1/Combined Data.csv
lab2/data2/medical_tc_train.csv
lab2/data2/medical_tc_test.csv
lab2/data2/medical_tc_labels.csv
```

For Lab 3, copy the `data2` folder next to the notebook (`lab3/data2/`).

## How to run

```bash
python3 -m venv env
source env/bin/activate
pip install jupyter pandas scikit-learn matplotlib seaborn graphviz spacy
python -m spacy download en_core_web_sm
jupyter notebook
```

Lab 1 also needs the Graphviz system package (`sudo apt install graphviz` on Debian/Ubuntu). Some cells of Labs 2 and 3 take several minutes (ensemble models), so avoid "Restart & Run All" unless needed.

## Tools

Python 3, pandas, NumPy, scikit-learn, spaCy, Matplotlib, seaborn, Graphviz, Jupyter.
