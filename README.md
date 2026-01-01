
<img width="526" height="361" alt="Screenshot 2025-12-31 at 4 38 40 PM" src="https://github.com/user-attachments/assets/f09e59b5-785c-472d-ac04-e9e154ee8bff" />

# Credit_card_FraudDetection
In an increasingly digital global economy, credit card fraud has evolved from simple theft into a multi-billion dollar criminal enterprise.Traditional security systems rely on static rules—pre-defined "if/then" scenarios that can only catch known threats. However, modern fraudsters are adaptive, constantly shifting their tactics to bypass these rigid boundaries.
**Power of machine learning in detecting fraud**
Machine learning provides a powerful solution to this problem by analyzing thousands of data points—such as transaction velocity, geographical mismatches, and spending patterns—in real-time.
ML models can simultaneously correlate a transaction with thousands of subtle variables—such as the micro-seconds between clicks, geographical inconsistencies, and device fingerprints—to spot microscopic anomalies that escape the human eye.Criminals change their patterns daily. It provides an evolving shield; as new data flows into the system, the model refines its understanding of "normal" versus "suspicious" behavior. It learns from every transaction, effectively future-proofing  security posture  of institutions against emerging fraud vectors before they become widespread.


**Project Overview: A Comparative Benchmark of ML Architectures for Fraud Detection**
This project provides a rigorous, data-driven comparison of three industry-standard Machine Learning (ML) architectures to identify fraudulent credit card transactions. Recognizing that financial fraud is a "needle-in-a-haystack" problem, this study evaluates how different mathematical approaches—ranging from linear classifiers to ensemble methods—handle extreme class imbalance and high-cardinality data.


Below walkthrough covers the end-to-end engineering process—from the intelligent synthesis of data to the final validation of a high-performance predictive pipeline.

1)**Data Synthesis Strategy: Beyond Anonymization**
A primary challenge in developing fraud detection models is the scarcity of high-fidelity, real-world data. Due to strict privacy regulations and security protocols, most available public datasets (such as those found on Kaggle) have undergone Principal Component Analysis (PCA). While PCA-transformed data is useful for mathematical modeling, it masks the actual feature names, making it impossible to gain an intuitive understanding of why a model flags a specific transaction.

To solve this, we utilized the Faker library to architect a custom, high-fidelity synthetic dataset. By synthesizing data from the ground up, we maintain full visibility into the features, allowing us to see exactly how variables like "merchant category" or "geographical mismatch" shape the model’s decision-making process.

**2) Data Preparation**

We begin by importing the synthesized transaction dataset using pd.read_csv and performing an initial inspection to understand the data structure, feature types, and class distribution.

Next, we construct the feature matrix X by removing the target column (fraud_label), which indicates whether a transaction is fraudulent or legitimate. The target variable y is defined separately as df['fraud_label'].

Since the dataset is highly imbalanced, with fraudulent transactions representing a very small fraction of the total data, we apply stratified sampling during the train–test split. Stratification ensures that both training and testing sets preserve the original class distribution, allowing the model to learn fraud patterns effectively and preventing bias toward the majority (non-fraudulent) class.

**3) Preprocessing**

Features are grouped by type and cardinality for efficient preprocessing. High-cardinality identifier columns (card_id, user_id, merchant_id) are dropped to avoid excessive dimensionality. Low-cardinality categorical features are one-hot encoded, numerical features are standardized, and boolean indicators are passed through unchanged. All transformations are applied using a ColumnTransformer to ensure a consistent and reproducible preprocessing pipeline.

**4) Model Implementation and Evaluation**

Three machine learning models—Logistic Regression, Random Forest, and XGBoost—are implemented using separate preprocessing–model pipelines to ensure consistent and fair comparison. For each model, a classification report is generated, including accuracy, precision, recall, and ROC–AUC metrics.

Each evaluation metric provides a distinct perspective on model performance: accuracy measures overall correctness, precision reflects the reliability of fraud predictions, recall assesses the model’s ability to detect fraudulent transactions, and ROC–AUC evaluates class separability across decision thresholds. Model performance is further analyzed using visualizations such as confusion matrices and bar charts, enabling intuitive comparison and interpretability.
