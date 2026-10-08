# Fungal Image Classification

I was doing this individual project by during April–June 2025. I compared three classical machine learning classifiers on 9,114 DeFungi microscopy images across five classes.

## Workflow
- Batch image preprocessing with Python and OpenCV: resizing to 80 x 80 and gamma adjustment; additional CLAHE contrast enhancement and bilateral filtering for training images.
- Combine 96 colour-histogram features with HOG (Histogram of Oriented Gradients) features.
- Compare Gaussian Naive Bayes, Linear SVC and Decision Tree using scikit-learn pipelines.
- Tune hyperparameters using nested stratified cross-validation: five outer folds and three inner folds, selecting by accuracy.
- Visualise fold-wise accuracy, macro-F1, train–test gaps and accuracy–runtime trade-offs with Matplotlib.

## Recorded results
Results below are from the original coursework report and saved notebook outputs, not a new training run.

| Model | Mean outer-fold accuracy | Mean macro-F1 |
|---|---:|---:|
| Gaussian Naive Bayes | 0.534 | 0.318 |
| Linear SVC | 0.455 | 0.357 |
| Decision Tree | 0.408 | 0.249 |

Naive Bayes had the highest accuracy while Linear SVC had the highest macro-F1. Class imbalance makes both metrics relevant. Training and test preprocessing differ, so train–test gaps alone do not establish overfitting. Measured runtime includes hyperparameter search, fitting and prediction, rather than single-image inference latency. The original decision tree has no fixed random seed, and dependencies are unpinned, so exact reproduction is not guaranteed.

## Run
1. Use Python 3.11 (the original README specifies 3.11.9).
2. Install dependencies: `pip install -r requirements.txt`.
3. Obtain DeFungi separately from its [UCI dataset page](https://archive.ics.uci.edu/dataset/773/defungi), observing its access and licence terms.
4. Place image class folders H1, H2, H3, H5 and H6 under `defungi/`, beside `code.ipynb`.
5. Open `code.ipynb` in Jupyter and run in order. The first processing cell creates `defungiPreprocessed/`.

The sampling multiplier in the notebook is 1 (all images), despite an older comment referring to 60%. No model training was repeated during repository preparation; code-cell syntax was checked. Saved outputs and notebook metadata were cleared for publication. Dataset images and the original report are not included. This repository documents a coursework experiment, not a deployed diagnostic application.
