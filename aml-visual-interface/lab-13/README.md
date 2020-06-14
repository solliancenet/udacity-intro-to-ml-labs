# Lab Overview

[Azure Machine Learning designer](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-designer) (preview) gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning designer also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications.

In this lab, we will be using the `Weather Dataset` that has weather data for 66 different airports in the USA from April to October 2013. We will cluster the dataset into 5 distinct clusters based on key weather metrics, such as visibility, temperature, dew point, wind speed etc. The goal is to group airports with similar weather conditions. We will do all of this from the Azure Machine Learning designer without writing a single line of code.

# Exercise 1: Create New Training Pipeline

## Task 1: Open Pipeline Authoring Editor

1. In [Azure portal](https://portal.azure.com/), open the available machine learning workspace.

2. Select **Launch now** under the **Try the new Azure Machine Learning studio** message.

    ![Launch Azure Machine Learning studio.](images/01a.png 'Launch AML')

3. When you first launch the studio, you may need to set the directory and subscription. If so, you will see this screen:

    ![Launch Azure Machine Learning studio.](images/00.png 'Launch AML')

    > For the directory, select **Udacity** and for the subscription, select **Azure Sponsorship**. For the machine learning workspace, you may see multiple options listed. **Select any of these** (it doesn't matter which) and then click **Get started**.

4. From the studio, select **Designer, +**. This will open a `visual pipeline authoring editor`.

   ![Image highlights the steps to open the pipeline authoring editor.](images/09.png 'Pipeline Authoring Editor')

## Task 2: Setup Compute Target

1. In the settings panel on the right, select **Select compute target**.

    ![Image highlights the link to select to open the setup compute target editor.](images/10.png 'Setup Compute Target')

2. In the `Set up compute target` editor, select the available compute, and then select **Save**.

    ![Image shows how to select the existing compute target named qs-compute.](images/11.png 'Setup Compute Target')

## Task 3: Add Dataset

1. Select **Datasets** section in the left navigation. Next, select **Samples, Weather Dataset** and drag and drop the selected dataset on to the canvas.

    ![Image shows the dataset, Weather Dataset, added to the canvas.](images/12.png 'Add Dataset')

## Task 4: Select Columns in Dataset

1. Select **Data Transformation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Select Columns in Dataset** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Weather Dataset` module to the `Select Columns in Dataset` module

    4. Select **Edit column** link to open the `Select columns` editor

    ![Image shows the steps to add and configure the Select Columns in Dataset module.](images/13_1.png 'Select Columns in Dataset Module')

    *Note that you can run the pipeline at any point to peek at the outputs and activities. Running pipeline also generates metadata that is available for downstream activities such selecting column names from a list in selection dialogs.*

2. In the `Select columns` editor, follow the steps outlined below:

    1. Include: **Column indices**

    2. Provide column indices: **8, 10-17, 20, 26**

    3. Select **Save**

    ![Image shows the steps to configure the Select Columns in Dataset module.](images/13_2.png 'Select columns')

## Task 5: Normalize Data

1. Select **Data Transformation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Normalize Data** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Select Columns in Dataset` module to the `Normalize Data` module

    4. Select **Edit column** link to open the `Columns to transform` editor

    ![Image shows the steps to add and configure the Normalize Data module.](images/13_3.png 'Normalize Data')

2. In the `Columns to transform` editor, follow the steps outlined below:

    1. Include: **All columns**

    2. Select **Save**

    ![Image shows the steps to configure the Normalize Data module.](images/13_4.png 'Columns to transform')

## Task 6: Initialize K-Means Clustering Model

1. Select **Machine Learning Algorithms** section in the left navigation. Follow the steps outlined below:

    1. Select the **K-Means Clustering** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Number of centroids: **5**

    ![Image shows the steps to add and configure the K-Means Clustering module.](images/14.png 'K-Means Clustering Module')

## Task 7: Setup Train Clustering Model Module

1. Select **Model Training** section in the left navigation. Follow the steps outlined below:

    1. Select the **Train Clustering Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `K-Means Clustering` module to the first input of the `Train Clustering Model` module

    4. Connect the first output of the `Normalize` module to the second input of the `Train Clustering Model` module

    5. Select the **Edit column** link to open the `Column set` editor

    ![Image shows the steps to add and configure the Train Clustering Model module.](images/15.png 'Train Clustering Model Module')

2. In the `Columns set` editor, follow the steps outlined below:

    1. Include: **All columns**

    2. Select **Save**

    ![Image shows the Columns set editor and how include all columns.](images/16.png 'Columns set')

## Task 8: Setup Assign Data to Clusters Module

1. Select **Model Scoring & Evaluation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Assign Data to Clusters** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the first output of the `Train Clustering Model` module to the first input of the `Assign Data to Clusters` module

    4. Connect the first output of the `Normalize Data` module to the second input of the `Assign Data to Clusters` module

    ![Image shows the steps to add and configure the Assign Data to Clusters module.](images/17.png 'Assign Data to Clusters')

# Exercise 2: Run Training Pipeline

## Task 1: Create Experiment and Run Pipeline

1. Select **Run** to open the `Setup pipeline run` editor.

    ![Image shows where to select the run button to open the setup pipeline run editor.](images/19.png 'Run Pipeline')

2. In the `Setup pipeline run` editor, select **+New experiment**, provide `Experiment Name:` **cluster-weather**, and then select **Run**.

    ![Image shows how to provide the experiment name in the setup pipeline run editor and start the pipeline run.](images/20.png 'Run Pipeline')

3. Wait for pipeline run to complete. It will take around **5 minutes** to complete the run.

4. While you wait for the model training to complete, you can learn more about the K-Means Clustering algorithm used in this lab by selecting [K-Means Clustering](https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/k-means-clustering#configure-the-k-means-clustering-module).

# Exercise 3: Visualize the Clustering Results

## Task 1: Open the Visualization Dialog

1. Select **Assign Data to Clusters, Outputs, Visualize** to open the `Assign Data to Clusters result visualization` dialog.

    ![Image shows how to open the Assign Data to Clusters result visualization dialog.](images/23.png 'Evaluate Model Results')

## Task 2: Evaluate Clustering Results

1. Scroll to the right and select **Assignments** column.

2. In the right-hand-side pane, scroll down to the **Visualizations** section.

    ![Image shows the Assign Data to Clusters result visualization dialog.](images/24.png 'Clustering Results')

3. From the results you can observe that each row (input) in the dataset is assigned to one of the 5 clusters: 0, 1, 2, 3, or 4. You can also see for each input, how far that input was from the various centroids. The cluster assignment is made based on the shortest distance between the input and cluster centroids. From the bar graph you can see the frequency distribution of all the inputs across the 5 clusters.

# Next Steps
Congratulations! You have trained and evaluated your first clustering algorithm. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.
