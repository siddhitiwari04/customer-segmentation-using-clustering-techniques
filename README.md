# Customer Segmentation using Unsupervised Learning

This project explores customer behavior in a shopping mall by grouping shoppers into meaningful segments based on their demographics and purchase patterns. The analysis uses clustering techniques to uncover patterns in age, annual income, spending behavior, and gender, with a focus on business-friendly segmentation and model validation.

The workflow in the notebook goes beyond a basic K-Means demo and includes:

- Exploratory data analysis and feature distribution checks
- Elbow method for identifying the appropriate number of clusters
- K-Means clustering on different feature combinations
- Cluster validation using silhouette score and Davies-Bouldin index
- Hierarchical clustering for comparison
- DBSCAN for outlier detection and density-based segmentation
- 2D and 3D cluster visualizations for interpretation

---

## Project Overview

Customer segmentation is a core marketing analytics task. Instead of treating all customers as one homogeneous group, the project identifies distinct customer cohorts that can be targeted with tailored promotions, loyalty offers, and retention strategies.

In this dataset, the key behavioral signal is the relationship between annual income and spending score, which reveals natural patterns that are ideal for clustering.

---

## Dataset

The project uses the file `Mall_Customers.csv`, containing 200 customer records and five variables:

| Column | Description |
| --- | --- |
| CustomerID | Unique customer identifier |
| Gender | Male or Female |
| Age | Customer age |
| Annual Income (k$) | Annual income in thousands of dollars |
| Spending Score (1-100) | Mall-assigned score reflecting purchasing behavior |

The notebook removes `CustomerID` before clustering, since it is not a meaningful feature for behavioral segmentation.

---

## Tools and Libraries

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- SciPy
- Jupyter Notebook

---

## Analysis Workflow

### 1. Data Cleaning and EDA

The notebook starts with a standard exploratory analysis:

- dataset shape and summary statistics
- checking dtypes and missing values
- removing irrelevant identifiers
- visualizing distributions of age, annual income, and spending score
- comparing gender distribution
- analyzing spread by age, income, and spending using violin plots

### 2. Feature Distribution Insights

Several visualizations reveal the dataset structure:

- Age is concentrated in the 20s to 40s, with the largest group in the 26–35 bracket
- Annual income is spread across a wide range, with a moderate concentration in the mid-income bands
- Spending score is fairly diverse, suggesting customers are not uniformly behaving the same way
- Gender distribution is slightly skewed toward female shoppers

### 3. Elbow Method for Cluster Selection

The notebook applies the elbow method to determine suitable cluster counts for different feature sets:

- Age vs. Spending Score → recommended `k = 4`
- Income vs. Spending Score → recommended `k = 5`
- All features (Age, Income, Spending Score) → recommended `k = 5`

This step helps balance model simplicity with cluster separation quality.

### 4. K-Means Clustering

K-Means is applied to several feature combinations to identify customer groups.

#### Age vs. Spending Score

This view highlights segmentation by life stage and consumer spending behavior. Younger customers split into low- and high-spending groups, while older groups are more tightly clustered around moderate spending patterns.

#### Annual Income vs. Spending Score

This is the most business-relevant view. The notebook identifies five distinct customer segments:

- High income, high spending
- High income, low spending
- Low income, high spending
- Low income, low spending
- Average income, average spending

These categories are highly actionable for marketing and revenue strategy.

#### All Features (3D clustering)

The final clustering uses all three major features together and produces a 3D view of the segmentation structure, confirming that the five-cluster pattern remains meaningful when age is included in the model.

---

## Cluster Validation

The notebook does not rely only on the elbow method. It quantifies the quality of cluster assignments using two standard metrics:

- Silhouette Score: higher is better
- Davies-Bouldin Index: lower is better

These metrics are computed across values of `k` for each feature set. The results align with the elbow-based choices, reinforcing that `k = 5` is a strong choice for the income/spending segmentation and for the full multivariate segmentation.

---

## Comparison of Clustering Methods

### K-Means

- Requires a predefined number of clusters
- Performs very well on the income–spending feature set
- Produces clean, interpretable segments

### Hierarchical Clustering

- Does not require specifying `k` upfront
- Builds a dendrogram and then cuts the tree at a meaningful point
- In this dataset, it produces a structure very similar to K-Means

### DBSCAN

- Density-based, not centroid-based
- Useful for detecting outliers and unusual customer profiles
- Identifies noise points that do not fit any dense segment
- Valuable when a business wants to flag atypical behavior rather than force every customer into a segment

This gives a more complete clustering picture than a single algorithm alone.

---

## Key Business Insights

The results provide several actionable observations:

- The mall has a strong base of customers in the mid-income and mid-spending ranges
- There are clear premium customer groups who spend heavily despite being in higher income bands
- Some high-income customers spend relatively little, suggesting potential upsell or conversion opportunities
- Low-income, high-spending customers represent a price-sensitive but high-potential segment for targeted promotions
- Customers in the 26–35 age group form a major segment of the customer base
- Gender differences are present, especially in spending behavior, which may inform campaign design

---

## Repository Structure

```text
.
├── Mall_Customers.csv
├── Customer_Segmentation.ipynb
├── Customer_Segmentation1.ipynb
├── README.md
└── assets/
    └── notebook_plots/
```

---

## How to Run

```bash
# Clone the repository
# cd into the project folder

# Install dependencies
pip install numpy pandas matplotlib seaborn scikit-learn scipy jupyter

# Launch the notebook
jupyter notebook Customer_Segmentation1.ipynb
```

---

## Conclusion

This project demonstrates how unsupervised learning can transform raw customer data into actionable business intelligence. The notebook shows that a mall customer base is not one uniform group, but a collection of distinct segments with different spending motivations, income levels, and age profiles.

By combining exploratory analysis, clustering, and quantitative validation, the project delivers a practical segmentation framework that can be used for marketing strategy, customer targeting, and business decision-making.

---

## Author

Siddhi Tiwari
