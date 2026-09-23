# Customer-Segmentation
This project demonstrates how to perform customer segmentation using transactional data from an online retail store. Customer segmentation helps businesses understand different customer profiles and improve their marketing strategies by grouping customers based on their behavior.

## Table of Contents
- [Project Overview](#Project-Overview)
- [Dataset](#Dataset)
- [Data Cleaning and Preprocessing](#Data-Cleaning-and-Preprocessing)
- [Machine Learning Models](#machine-learning-models)
- [Results](#results)


## Project Overview
The problem statement is
A retailer requires to create customer clusters, which are "customer segments" through a data-driven approach. Currently, the retailer simply groups their international customers by country which is very inefficient way of segmentation. They have provided a dataset of past transaction-level purchase data, aiming to segment customers based on buying patterns.

The goal of this project is to cluster customers based on their purchasing behavior using unsupervised machine learning techniques. Using clustering algorithms such as K-Means to group customers into different segments based on key features derived from their transactional data, where the clustering model factors in both aggregate sales patterns and specific items purchased.


## Dataset
The dataset has 35116 observations for previous international transactions.
The observations span 37 different countries.

We have the following features:

Invoice information

- 'InvoiceNo' – Unique ID for invoice
- 'InvoiceDate' – Invoice date

Item information

- 'StockCode' – Unique ID for item
- 'Description' – Text description for item
- 'Quantity' – Units per pack for item
- 'UnitPrice' – Price per unit in GBP

Customer information

- 'CustomerID' – Unique ID for customer
- 'Country' – Country of customer

## Data Cleaning and Preprocessing

Handling Missing Values: Rows with missing CustomerID were removed.

Feature Engineering: New features were created such as Sales which was unit price* quantity

The first step involves grouping data at the customer level to capture essential purchase patterns. For each customer, the folowing was calculated:
- The total number of transactions they made.
- The number of unique products they purchased.
- The average value of the products they bought.
- The total sales generated from their purchases.
- The average cart value, representing the average total cost of the items in each transaction.

Then at product-level, it was determined how much of each product a customer purchased. To streamline this process, a threshold was applied to focus on the top 150 most frequently purchased products. This ensures that the segmentation model factors in the most impactful buying behavior, without being overwhelmed by less relevant products.

## Machine Learning Models
### PCA
Principal Component Analysis (PCA) is an Unsupervised Learning task that creates a sequence of new, uncorrelated features that each try to maximize its "explained variance" of the original dataset.

It does so by generating linear combinations from your original features and these new features are meant to replace the original ones.
Based on the cummulative varience graph formed, to capture about 98% of the variance, it was required to keep around 300 components. Thus, reducing the dimensionality from 2574 to 300 features that explained the most variance for the original features.

### KMeans Clustering
 K-Means creates clusters based on distances that calculated by between observations defined by their feature values.
 3 possible feature sets were take and clusters created from them were compared. These are:

- Only purchase pattern features ("Base DF")
- Purchase pattern features + item features chosen by thresholding ("Threshold DF")
- Purchase pattern features + principal component features from items ("PCA DF")

## Results
The analysis can determine the similarities between different segmentation approaches. This is important for businesses because it helps in evaluating the effectiveness of different strategies and understanding the relationship between various customer segments. For example, if a business wants to switch from one customer segmentation method to another method, analyzing the overlap or differences between the two segmentations can provide valuable insights.

- By comparing different segmentation techniques, businesses can see which customers consistently fall into similar groups.
- If two segmentation approaches yield similar clusters, businesses can apply the same or slightly modified marketing strategies to target these groups.
- It can help a business to gauge the potential impact of a strategy shift.
