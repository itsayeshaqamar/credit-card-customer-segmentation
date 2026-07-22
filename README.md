<img width="212" height="212" alt="logo" src="https://github.com/user-attachments/assets/e9b2db24-18ac-4eaf-83ee-58253fec7f5c" />

# Credit Card Customer Segmentation using K-Means and Hierarchical Clustering

## Project Overview

This project focuses on **customer segmentation** using unsupervised machine learning techniques. The objective is to group credit card customers with similar spending and financial behaviors into meaningful segments. Customer segmentation helps financial institutions better understand customer behavior, improve marketing strategies, provide personalized services, and support data-driven business decisions.

Two clustering algorithms were implemented and compared:

- **Part 1:** K-Means Clustering
- **Part 2:** Agglomerative Hierarchical Clustering

The performance and results of both algorithms were analyzed to determine the most suitable clustering approach for this dataset.

---

# Dataset Information

- **Dataset:** Credit Card Customer Segmentation Dataset
- **Total Records:** 8,950 customers
- **Original Features:** 18
- **Features Used for Clustering:** 17
- **Target Variable:** None (Unsupervised Learning)

The dataset contains customer information related to:

- Account balance
- Purchase behavior
- One-off purchases
- Installment purchases
- Cash advances
- Purchase frequency
- Credit limit
- Payments
- Minimum payments
- Full payment percentage
- Account tenure

Since clustering is an unsupervised learning task, there is no target variable.

---

# Project Objectives

The objectives of this project are:

- Explore and understand customer financial behavior.
- Prepare the dataset through preprocessing.
- Apply K-Means Clustering for customer segmentation.
- Determine the optimal number of clusters.
- Visualize clustering results.
- Perform Hierarchical Clustering.
- Compare both clustering techniques.
- Interpret customer segments from a business perspective.

---

# Technologies and Libraries Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- SciPy

---

# Project Structure

```
credit-card-customer-segmentation/
│
├── notebooks/
│   └── week4_clustering.ipynb
│
├── data/
│   └── dataset(w4).csv
│
├── README.md
│
└── requirements.txt
```

---

# Part 1 – K-Means Clustering

## Step 1: Data Loading and Exploration

The dataset was loaded into Pandas and explored to understand its structure.

The following information was examined:

- Dataset shape
- Column names
- Data types
- Dataset information
- Preview of the first few records

The customer ID column was removed because it does not contribute to clustering.

---

## Step 2: Missing Value Analysis

The dataset was checked for missing values.

Missing values were found in:

- CREDIT_LIMIT
- MINIMUM_PAYMENTS

Since both columns are numerical, missing values were replaced using the **median**, which is less sensitive to outliers than the mean.

After imputation, the dataset contained no missing values.

---

## Step 3: Feature Scaling

The dataset was standardized using **StandardScaler**.

Standardization transforms every feature so that:

- Mean ≈ 0
- Standard Deviation ≈ 1

Feature scaling ensures that all variables contribute equally to distance calculations used by clustering algorithms.

---

## Step 4: Applying K-Means Clustering

The K-Means algorithm was trained using different numbers of clusters ranging from **2 to 10**.

For each value of **k**, the inertia value was calculated.

---

## Step 5: Elbow Method

The Elbow Method was used to determine the optimal number of clusters.

The inertia values decreased as the number of clusters increased. The elbow point appeared at **k = 3**, indicating that three clusters provide a good balance between model simplicity and cluster quality.

---

## Step 6: Silhouette Score

The Silhouette Score was calculated for each value of **k**.

The highest score was obtained at:

- **k = 3**
- **Silhouette Score ≈ 0.251**

This confirmed that three clusters produced the best cluster separation.

---

## Step 7: Final K-Means Model

The final K-Means model was trained using:

- Number of clusters = 3

Each customer was assigned a cluster label.

Cluster distribution:

- Cluster 0: 1,275 customers (14.25%)
- Cluster 1: 6,114 customers (68.31%)
- Cluster 2: 1,561 customers (17.44%)

---

## Step 8: Cluster Profiling

The average value of each feature was calculated for every cluster.

A heatmap was generated to compare customer behavior across all clusters.

The cluster profiles revealed clear differences in:

- Purchase behavior
- Credit limits
- Cash advance usage
- Payment behavior
- Account balances

---

## Step 9: Customer Segment Interpretation

The clusters were interpreted from a business perspective.

### Cluster 0 – High Spending Customers

Characteristics:

- High purchases
- High purchase frequency
- High credit limit
- High payment amounts

Business Recommendation:

- Offer premium credit cards.
- Provide cashback and reward programs.
- Improve customer loyalty through exclusive offers.

---

### Cluster 1 – Low Activity Customers

Characteristics:

- Low balance
- Low purchases
- Lower credit limit
- Lower payment amounts

Business Recommendation:

- Encourage card usage through promotions.
- Offer discounts and introductory rewards.
- Launch personalized marketing campaigns.

---

### Cluster 2 – Cash Advance Customers

Characteristics:

- Highest balance
- Highest cash advance usage
- High credit limit
- Lower purchase activity than Cluster 0

Business Recommendation:

- Offer installment payment plans.
- Promote financial planning services.
- Encourage purchase-based transactions instead of cash advances.

---

# Part 2 – Hierarchical Clustering

## Step 1: Random Sampling

Since Hierarchical Clustering has a high computational cost, a random sample of **300 customers** was selected from the standardized dataset.

This reduced computation time while maintaining a representative sample.

---

## Step 2: Dendrogram Visualization

A dendrogram was created using the **Ward linkage method**.

A horizontal threshold line was added to identify the optimal cut.

The dendrogram showed approximately **three major clusters**, supporting the K-Means results.

---

## Step 3: Agglomerative Hierarchical Clustering

Agglomerative Clustering was applied using:

- Number of clusters = 3
- Ward linkage

Cluster distribution:

- Cluster 0: 39 customers
- Cluster 1: 98 customers
- Cluster 2: 163 customers

---

## Step 4: Comparison with K-Means

The cluster assignments produced by both algorithms were compared using **pd.crosstab()**.

The comparison showed that:

- Many customers were assigned to similar groups.
- Some differences existed due to the different clustering strategies used by each algorithm.
- Overall, both methods captured similar customer behavior patterns.

---

## Step 5: Comparison Report

Both clustering algorithms successfully identified meaningful customer segments.

### K-Means

Advantages:

- Faster
- Scalable
- Easy to interpret
- Suitable for large datasets
- Widely used in industry

### Hierarchical Clustering

Advantages:

- Provides dendrogram visualization.
- Helps understand relationships between clusters.
- Useful for exploratory data analysis.

However, Hierarchical Clustering is computationally more expensive and less suitable for very large datasets.

For this project, **K-Means is recommended** because it provides efficient, scalable, and interpretable customer segmentation.

---

# Results Summary

The project successfully identified three meaningful customer segments based on credit card usage behavior.

Major findings include:

- Three clusters provided the optimal segmentation.
- Standardization significantly improved clustering quality.
- The Elbow Method and Silhouette Score both supported selecting three clusters.
- Cluster profiling revealed distinct spending and financial behavior among customer groups.
- Hierarchical Clustering produced results similar to K-Means.
- K-Means proved to be the more practical algorithm for this business use case.

---

# Conclusion

This project demonstrated how unsupervised machine learning can be used to analyze customer behavior and perform effective customer segmentation.

Both K-Means and Agglomerative Hierarchical Clustering successfully grouped customers into meaningful segments. While Hierarchical Clustering provided valuable insights through the dendrogram, K-Means offered better scalability, faster execution, and easier interpretation.

The resulting customer segments can help financial institutions design targeted marketing campaigns, improve customer engagement, optimize financial products, and support strategic business decisions.

---

# How to Run the Project

1. Clone the repository.

```bash
git clone <repository-link>
```

2. Navigate to the project directory.

```bash
cd credit-card-customer-segmentation
```

3. Install the required libraries.

```bash
pip install -r requirements.txt
```

4. Open the notebook.

```bash
jupyter notebook
```

5. Run all cells in:

```
notebooks/week4_clustering.ipynb
```

---

# Author

**Ayesha Qamar**

AI/ML Internship – IT Simplera

Week 4 Assignment – Credit Card Customer Segmentation using K-Means and Hierarchical Clustering
