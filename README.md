# Assignment 4: Reject Option Classification on Adult, German and COMPAS

Code for Task 2 of the INFOMDW Data Wrangling assignment on bias mitigation (Thijme Bouwmeester).

This repository is a fork of [AIF360](https://github.com/Trusted-AI/AIF360). The notebook uses AIF360's implementation of
Reject Option based Classification (Kamiran, Karim & Zhang, ICDM 2012) as it is, installed from PyPI.
Only the notebook and this README are mine; the AIF360 files are removed to keep the repository simple.

`roc_mitigation.ipynb` is saved with all its outputs, so the results can be read without running it.
Its headings are the six steps of the assignment.

## How to run

Tested with Python 3.13. Internet is needed on the first run to download the data.

1. Clone the repository:

   ```
   git clone https://github.com/thijmebouwmeester-source/AIF360.git
   cd AIF360
   ```

2. Install the packages (AIF360 0.6.1 needs pandas below version 3):

   ```
   pip install aif360==0.6.1 "pandas<3" scikit-learn notebook
   ```

3. Open the notebook and run all cells (about 5 minutes):

   ```
   jupyter notebook roc_mitigation.ipynb
   ```

The first code cell downloads the datasets into AIF360's data folder.
If a download fails, save the file by hand in the folder that the error message shows:
[adult.data and adult.test](https://archive.ics.uci.edu/ml/machine-learning-databases/adult/),
[german.data](https://archive.ics.uci.edu/ml/machine-learning-databases/statlog/german/) and
[compas-scores-two-years.csv](https://github.com/propublica/compas-analysis).

## Expected results

A clean run gives exactly this table (Table 3 of the report).

| Dataset | Labels or predictions | DP_Diff | DIR | Consistency | Accuracy |
| --- | --- | ---: | ---: | ---: | ---: |
| Adult | Original labels (before) | -0.199 | 0.363 | 0.829 | – |
| | Test predictions without ROC | -0.186 | 0.290 | 0.945 | 0.850 |
| | Test predictions with ROC (after) | -0.042 | 0.733 | 0.955 | 0.834 |
| German | Original labels (before) | -0.149 | 0.795 | 0.740 | – |
| | Test predictions without ROC | -0.068 | 0.920 | 0.846 | 0.773 |
| | Test predictions with ROC (after) | -0.022 | 0.972 | 0.824 | 0.770 |
| COMPAS | Original labels (before) | -0.097 | 0.840 | 0.668 | – |
| | Test predictions without ROC | -0.169 | 0.764 | 0.858 | 0.671 |
| | Test predictions with ROC (after) | -0.071 | 0.893 | 0.855 | 0.663 |
