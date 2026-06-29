# OD-Abs: A one-class outlier detection-based approach for classifying images of bacteria and fungi from abscesses

This repository contains the code used to reproduce the final OD-Abs β-VAE experiments reported in the paper:

**OD-Abs: A one-class outlier detection-based approach for classifying images of bacteria and fungi from abscesses**

The provided notebooks cover the 5-fold cross-validation training of the selected β-VAE model and the evaluation of different threshold selection methods used for the final OD-Abs classifier.

## Repository Contents

```text
notebooks/
│
├── OD_Abs_Beta_VAE_training_5_fold_CV.ipynb
├── OD_Abs_Evaluation_comparison_of_different_threshold_methods.ipynb
│
└── README.md
```

The trained models and cross-validation results are made available separately through Google Drive:

```text
https://drive.google.com/drive/folders/1WqP3kNQAAfwbCnAis4PzELjk4qF69bIq?usp=sharing
```

The results folder contains the outputs for each fold:

```text
Cross Validation Final Results Beta-VAE/
│
├── fold_1/
│   ├── best_model.pth
│   └── test_results.csv
│
├── ...
│
└── final_comparison_results.csv
```

## Notebooks

### 1. `OD_Abs_Beta_VAE_training_5_fold_CV.ipynb`

This notebook trains the selected β-VAE model using a 5-fold cross-validation setup.

For each fold, the notebook saves:

* the best trained model weights: `best_model.pth`;
* the test predictions and reconstruction errors: `test_results.csv`.

### 2. `OD_Abs_Evaluation_comparison_of_different_threshold_methods.ipynb`

This notebook evaluates the trained β-VAE models using different threshold selection strategies.

It computes the final classification metrics reported for OD-Abs, including:

* precision;
* sensitivity;
* specificity;
* F1-score;
* AUC.

The notebook also compares thresholding based on:

* mean reconstruction error plus two standard deviations;
* grid search using the validation/tuning set.

## Dataset Preparation

The datasets are not redistributed in this repository. Please download the original datasets from their official sources and organize the images as described below.

The code expects two folders in the working directory:

```text
DeFungi Dataset/
DiBaSandDeepBacs/
```

The expected format is one flat folder per class. All images should be placed directly inside the corresponding folder.

Example:

```text
DeFungi Dataset/
├── H1_H1_100a_1.jpg
├── H1_H1_100a_2.jpg
├── H1_H1_100a_3.jpg
└── ...

DiBaSandDeepBacs/
├── Acinetobacter.baumanii_0001.tif
├── Acinetobacter.baumanii_0002.tif
├── Acinetobacter.baumanii_0003.tif
└── ...
```

## Running the Code

To reproduce the training and evaluation:

1. Prepare the dataset folders using the structure described above.
2. Open `OD_Abs_Beta_VAE_training_5_fold_CV.ipynb`.
3. Run the cells from top to bottom.
4. After training, open `OD_Abs_Evaluation_comparison_of_different_threshold_methods.ipynb`.
5. Run the cells from top to bottom to compute the final evaluation metrics.

If using the provided trained models and saved results, download the Google Drive results folder and make sure it is placed in the expected path before running the evaluation notebook.

Depending on the working directory, the path to the results folder may need to be adjusted in the notebook. For example:

```python
BASE_OUTPUT_DIR = "Cross Validation Final Results Beta-VAE"
```

## Outputs

For each fold, the training notebook produces:

```text
best_model.pth
test_results.csv
```

The `test_results.csv` files contain the reconstruction errors, predicted labels, and true labels for the test samples of each fold.

The final comparison file:

```text
final_comparison_results.csv
```

summarizes the performance obtained using the evaluated threshold selection strategies.




Please refer to the repository license for terms of use.

