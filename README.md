## Multivariate Geochemical Classification

### Project Overview

This project aims to classify **geochemical samples from boreholes** into different stratigraphic units based on multivariate geochemical data. By analyzing the concentrations of various elements, the goal is to develop a machine learning model that can predict the geological layer (`Stratigraphy`) of a sample, aiding in geological mapping and mineral exploration.

-----

### Technical Highlights

  * **Dataset**: [Kaggle - Multivariate Geochemical Classification](https://www.kaggle.com/datasets/saurabhshahane/multivariate-geochemical-classification)
  * **Size**: 1205 entries, 23 columns
  * **Key Features**:
      * Concentrations of various elements (e.g., `Cr2O3_%`, `FeO_%`, `SiO2_%`, `MgO_%`, `Al2O3_%`, `CaO_%`, `P_%`, `Au_ICP_ppm`, `Pt_ICP_ppm`, etc.), as well as depth and borehole type.
  * **Approach**:
      * Data Cleaning: Dropped rows with missing values (`dropna`). Dropped `DepthTo` due to its high correlation with `DepthFrom` (as observed from a heatmap).
      * Exploratory Data Analysis: Histograms, Boxplots, and a heatmap were used for visualization to understand data distributions and correlations.
      * Label Encoding: Applied to all columns, including numerical ones and the target `Stratigraphy`.
      * Handling Class Imbalance with `SMOTE` (Synthetic Minority Over-sampling Technique) on the training data. This is crucial as the original dataset is highly imbalanced in its target classes (`Stratigraphy` has 15 unique values, and `Filter` which is the target in the code, is also highly imbalanced).
      * Binary Classification: The target variable `Filter` indicates a binary outcome (0 or 1), though the project title and a different column, `Stratigraphy`, suggest a multi-class problem. This README reflects the code's action of classifying `Filter`.
      * Models Used:
          * Logistic Regression, Ridge Classifier, SVC, Random Forest, XGBoost, AdaBoost, Gradient Boosting, Bagging, Decision Tree.
  * **Best Accuracy**:
      * 100% with XGBoost, Random Forest, AdaBoost, Gradient Boosting, Bagging, and SVC.
      * 99.8% with Decision Tree Classifier.
      * The extremely high accuracies for most models suggest that the features provide very strong discriminative power for the target variable `Filter`, or that there might be a data leakage issue.

-----

### Purpose and Applications

  * **Automate geochemical classification** in geological surveys and mineral exploration.
  * Reduce the time and cost associated with manual core logging and sample analysis.
  * Aid geologists in identifying different stratigraphic units and potential mineral deposits.
  * Support data-driven decision-making in the mining and resource sectors.

-----

### Installation

Clone the repository:

```bash
git clone https://github.com/BhaveshBhakta/Multivariate-Geochemical-classification-Using-ML.git
cd Multivariate-Geochemical-classification-Using-M
```

Install the necessary libraries:

```bash
pip install pandas numpy seaborn matplotlib scikit-learn imbalanced-learn xgboost
```

-----

### Collaboration

We welcome contributions to improve the project. You can help by:

  * **Clarifying the target variable**: A key task is to choose between `Filter` and `Stratigraphy` as the target and correctly set up the classification problem (binary vs. multi-class).
  * Investigating the very high accuracy for potential data leakage or an overly simple classification task.
  * Performing comprehensive hyperparameter tuning and cross-validation for all models.
  * Exploring more robust strategies for handling missing data, such as advanced imputation methods.
  * Adding explainability (e.g., SHAP or LIME) to understand which element concentrations are the most critical for geochemical classification.
