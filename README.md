This Jupyter notebook demonstrates the implementation of K-Means clustering on a U.S. crime dataset using Amazon SageMaker's built-in KMeans algorithm. Here’s what the notebook does step-by-step:

---

### 1. Data Acquisition

- The notebook downloads a CSV dataset (`crime.csv`) containing crime statistics for different U.S. states.

---

### 2. Data Preparation

- Loads the dataset into a pandas DataFrame (`crime`).
- Defines a function, `stateToNumber`, to convert state names into unique numeric codes (by summing hex values of their character codes).
- Replaces the 'State' column in the DataFrame with these numeric codes.
- Converts the DataFrame to a Numpy array of type `float32` for processing.

---

### 3. Feature Selection

- Slices the data to select relevant columns for clustering (columns 1-4, typically those representing different crime statistics).

---

### 4. Setting up Amazon SageMaker for Clustering

- Imports SageMaker modules.
- Acquires the AWS execution role and sets up S3 bucket paths for data input and output.
- Initializes a SageMaker KMeans estimator, configuring parameters including:
  - Number of clusters (`k=10`)
  - Instance type and count for training
  - Input and output S3 locations

---

### 5. Training the KMeans Model

- Trains the KMeans model on the selected crime data slice using SageMaker’s distributed training infrastructure.

---

### 6. Model Deployment and Prediction

- Deploys the trained KMeans model as a real-time endpoint on SageMaker.
- Supplies state data (crime statistics) to the endpoint predictor for clustering.
- The predictor assigns each state to its closest cluster.

---

### 7. Results Interpretation

- For each state, the notebook prints:
  - State identifier
  - State code
  - Closest cluster label
  - Crime statistics (murders, assaults, urban population, rapes)
- These outputs allow users to analyze how states are grouped based on their crime profiles.

---

### Summary

This notebook is a practical example of:
- Preprocessing tabular crime data (feature engineering and transformation)
- Using Amazon SageMaker for scalable K-Means training and deployment
- Assigning cluster labels to U.S. states according to their crime characteristics
- Presenting clustering results for interpretation and analysis

It covers the full pipeline: download data, clean and process data, train and deploy a model using cloud resources, and visualize results for clustering-based insights.
