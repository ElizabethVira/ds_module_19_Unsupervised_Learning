# ds_module_19_Unsupervised_Learning
Homework Module 19 - Machine Learning, Principal Component Analysis (PCA)
=========
Objective
----
The goal of this project is to put into practice machine learning, a type of artificial intelligence that utilizes algorithms and statistical models to make decisions or predictions based on data. For this project, we will focus on unsupervised learning, where algorithms analyze test data to build models that categorize the relationships among data points.

Real-life applications of unsupervised learning include:
- Categorizing articles into different news sections
- Text translation and classification
- Speech recognition in conversational interfaces

![alt text](./Images/Unsupervised_Learning-.PNG)

In this challenge, we will use the knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

Instructions
===
1. Rename the Crypto_Clustering_starter_code.ipynb file as Crypto_Clustering.ipynb.

2. Load the crypto_market_data.csv into a DataFrame.

3. Get the summary statistics and plot the data to see what the data looks like before proceeding.

Prepare the Data
===
- Use the StandardScaler() module from scikit-learn to normalize the data from the CSV file.

- Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

    - The first five rows of the scaled DataFrame should appear as follows:

    ![alt text](./Images/DataFrame_table.PNG)

Find the Best Value for k Using the Original Scaled DataFrame
===
Use the elbow method to find the best value for k using the following steps:

- Create a list with the number of k values from 1 to 11.
- Create an empty list to store the inertia values.
- Create a for loop to compute the inertia with each possible value of k.
- Create a dictionary with the data to plot the elbow curve.
- Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

- Answer the following question in your notebook: What is the best value for k?
![alt text](./Images/Elbow_Curve_graph.PNG)

Cluster Cryptocurrencies with K-means Using the Original Scaled Data
===
- Initialize the K-means model with the best value for k.
- Fit the K-means model using the original scaled DataFrame.
- Predict the clusters to group the cryptocurrencies using the original scaled DataFrame.
- Create a copy of the original data and add a new column with the predicted clusters.

- Create a scatter plot using hvPlot as follows:
    - Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
    - Color the graph points with the labels found using K-means.
    - Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

![alt text](./Images/Cluster_scatter_plot.PNG)

Optimize Clusters with Principal Component Analysis
===
- Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.

- Retrieve the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook:

    - What is the total explained variance of the three principal components?
- Create a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

    - The first five rows of the PCA DataFrame should appear as follows:

![alt text](./Images/PCA_Table.PNG)

Find the Best Value for k Using the PCA Data
===
Use the elbow method on the PCA data to find the best value for k using the following steps:

- Create a list with the number of k-values from 1 to 11.
- Create an empty list to store the inertia values.
- Create a for loop to compute the inertia with each possible value of k.
- Create a dictionary with the data to plot the Elbow curve.
- Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

- Answer the following question in your notebook:

    - What is the best value for k when using the PCA data?

    - Does it differ from the best k value found using the original data?

![alt text](./Images/Elbow_Curve_PCA_graph.PNG)

Cluster Cryptocurrencies with K-means Using the PCA Data
===
Use the following steps to cluster the cryptocurrencies for the best value for k on the PCA data:

- Initialize the K-means model with the best value for k.
- Fit the K-means model using the PCA data.
- Predict the clusters to group the cryptocurrencies using the PCA data.
- Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
![alt text](./Images/PCA_Clusters_table.PNG)

- Create a scatter plot using hvPlot as follows:
    - Set the x-axis as "PC1" and the y-axis as "PC2".
    - Color the graph points with the labels found using K-means.
    - Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

![alt text](./Images/Cluster_PCA_scatter_plot.PNG)

- Answer the following question:
    - What is the impact of using fewer features to cluster the data using K-Means?
    ```  * **Answer:** 
  * Comparing the cluster analysis plots, the market segmentation using the full DataFrame shows different results than the PCA analysis. The original DataFrame indicates that most coins have a high percentage change over 24 hours and 7 days, and the PCA analysis shows a low percentage change in these periods.
  
  * Talking abou the value of `k` is consistent whether using the elbow method on the original data or the PCA data.