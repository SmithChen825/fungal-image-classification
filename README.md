# Fungal Image Classification

I completed this individual project during April–June 2025. I compared three classical machine learning classifiers on 9,114 DeFungi microscopy images across five classes.

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

Naive Bayes had the highest accuracy while Linear SVC had the highest macro-F1. Class imbalance makes both metrics relevant.

## Interpretation and reproducibility

- Training and test preprocessing differ, so train–test gaps alone do not establish overfitting.
- Runtime includes hyperparameter search, fitting and prediction; it is not single-image inference latency.
- Splits are stratified at image level, not grouped by source specimen; this experiment does not establish generalisation to unseen patients or specimens.
- The original decision tree has no fixed random seed, and dependencies are unpinned, so exact results may vary.

## Run
1. Use Python 3.11 (the original README specifies 3.11.9).
2. Install dependencies: `pip install -r requirements.txt`.
3. Obtain DeFungi separately from its [UCI dataset page](https://archive.ics.uci.edu/dataset/773/defungi), observing its access and licence terms.
4. Place image class folders H1, H2, H3, H5 and H6 under `defungi/`, beside `code.ipynb`.
5. Open `code.ipynb` in Jupyter and run in order. The first processing cell creates `defungiPreprocessed/`.

## Dataset acknowledgement and citation

This project uses **DeFungi**, created by **Camilo Javier Pineda Sopo, Farshid Hajati and Soheila Gheisari**. Credit for the dataset belongs to its creators; my contribution is the preprocessing, feature extraction, model comparison and analysis in this repository.

- Dataset source: [DeFungi — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/773/defungi).
- Dataset licence: [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), as listed by UCI.
- Associated paper: Pineda Sopo, C. J., Hajati, F., & Gheisari, S. (2021). *DeFungi: Direct Mycological Examination of Microscopic Fungi Images*. [https://doi.org/10.48550/arXiv.2109.07322](https://doi.org/10.48550/arXiv.2109.07322).

Images are processed locally using resizing, gamma adjustment and the training-image enhancements described above. Neither the original images nor processed copies are redistributed here. The dataset licence applies to the dataset; it does not automatically license this repository's code.

## Repository notes

The sampling multiplier in the notebook is 1 (all images), despite an older comment referring to 60%. Saved outputs and notebook metadata were cleared for publication. Code-cell syntax was checked; model training was not repeated during repository preparation. The original coursework report is not included. This repository documents an educational experiment, not a deployed diagnostic application.
