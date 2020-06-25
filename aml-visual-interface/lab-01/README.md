# Lab Overview

[Azure Machine Learning designer](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-designer) (preview) gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning designer also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications.

In this lab, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. Based on the enriched dataset, we will learn to use the Azure Machine Learning Graphical Interface to process data, build, train, score, and evaluate a regression model to predict NYC taxi fares. To train the model, we will create Azure Machine Learning Compute resource. We will do all of this from the Azure Machine Learning designer without writing a single line of code.

# Exercise 1: Register Dataset with Azure Machine Learning studio

## Task 1: Upload Dataset

1. In [Azure portal](https://portal.azure.com/), open the available machine learning workspace.

2. Select **Launch now** under the **Try the new Azure Machine Learning studio** message.

    ![Launch Azure Machine Learning studio.](images/01a.png 'Launch AML')

3. When you first launch the studio, you may need to set the directory and subscription. If so, you will see this screen:

    ![Launch Azure Machine Learning studio.](images/00.png 'Launch AML')

    > For the directory, select **Udacity** and for the subscription, select **Azure Sponsorship**. For the machine learning workspace, you may see multiple options listed. **Select any of these** (it doesn't matter which) and then click **Get started**.

4. From the studio, select **Datasets, + Create dataset, From web files**. This will open the `Create dataset from web files` dialog on the right.

   ![Image highlights the steps to open the create dataset from web files dialog.](images/04.png 'Create dataset from web files')

5. In the Web URL field provide the following URL for the training data file:
    ```
    https://introtomlsampledata.blob.core.windows.net/data/nyc-taxi/nyc-taxi-sample-data.csv
    ```
6. Provide `nyc-taxi-sample-data` as the Name, leave the remaining values at their defaults and select **Next**.

    ![Upload nyc-taxi-sample-data.csv from a URL.](images/05.png 'Upload dataset')

## Task 2: Preview Dataset

1. On the Settings and preview panel, set the column headers drop down to `All files have same headers`.

2. Scroll the data preview to right to observe the target column: `totalAmount`. After you are done reviewing the data, select **Next**

    ![Scroll right to review dataset.](images/06.png 'Review dataset')

## Task 3: Select Columns

1. Select columns from the dataset to include as part of your training data. Leave the default selections and select **Next**

    ![Select columns from the dataset to include as part of your training data.](images/07.png 'Select columns')

## Task 4: Create Dataset

1. Confirm the dataset details and select **Create**

    ![Confirm the details of the dataset you uploaded and then select Create.](images/08.png 'Confirm and create the dataset')

# Exercise 2: Create New Training Pipeline

## Task 1: Open Pipeline Authoring Editor

1. From the studio, select **Designer, +**. This will open a `visual pipeline authoring editor`.

   ![Image highlights the steps to open the pipeline authoring editor.](images/09.png 'Pipeline Authoring Editor')

## Task 2: Setup Compute Target

1. In the settings panel on the right, select **Select compute target**.

    ![Image highlights the link to select to open the setup compute target editor.](images/10.png 'Setup Compute Target')

2. In the `Set up compute target` editor, select the available compute, and then select **Save**.`NOTE : If you are facing any difficulties in accessing any of the pop-up windows properly or any of the buttons, Please refer to the Help section in the lab environment`

    ![Image shows how to select the existing compute target named qs-compute.](images/11.png 'Setup Compute Target')

## Task 3: Add Dataset

1. Select **Datasets** section in the left navigation. Next, select **My Datasets, nyc-taxi-sample-data** and drag and drop the selected dataset on to the canvas.

    ![Image shows the dataset, nyc-taxi-sample-data, added to the canvas.](images/12.png 'Add Dataset')

## Task 4: Split Dataset

1. Select **Data Transformation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Split Data** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Fraction of rows in the first output dataset: **0.7**

    4. Connect the `Dataset` to the `Split Data` module

    ![Image shows the steps to add and configure the Split Data module.](images/13.png 'Split Data Module')

*Note that you can submit the pipeline at any point to peek at the outputs and activities. Running pipeline also generates metadata that is available for downstream activities such selecting column names from a list in selection dialogs.*

## Task 5: Initialize Regression Model

1. Select **Machine Learning Algorithms** section in the left navigation. Follow the steps outlined below:

    1. Select the **Linear Regression** prebuilt module

    2. Drag and drop the selected module on to the canvas

    ![Image shows the steps to add and configure the Linear Regression module.](images/14.png 'Linear Regression Module')

## Task 6: Setup Train Model Module

1. Select **Model Training** section in the left navigation. Follow the steps outlined below:

    1. Select the **Train Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Linear Regression` module to the first input of the `Train Model` module

    4. Connect the first output of the `Split Data` module to the second input of the `Train Model` module

    5. Select the **Edit column** link to open the `Label column` editor

    ![Image shows the steps to add and configure the Train Model module.](images/15.png 'Train Model Module')

2. The `Label column` editor allows you to specify your `Label or Target column`. Type in the label column name **totalAmount** and then select **Save**.

    ![Image shows the label column editor and how to provide the label column name.](images/16.png 'Label Column')

## Task 7: Setup Score Model Module

1. Select **Model Scoring & Evaluation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Score Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Train Model` module to the first input of the `Score Model` module

    4. Connect the second output of the `Split Data` module to the second input of the `Score Model` module

    ![Image shows the steps to add and configure the Score Model module.](images/17.png 'Score Model')

*Note that `Split Data` module will feed data for both model training and model scoring. The first output (0.7 fraction) will connect with the `Train Model` module and the second output (0.3 fraction) will connect with the `Score Model` module.*

## Task 8: Setup Evaluate Model Module

1. Select **Model Scoring & Evaluation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Evaluate Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Score Model` module to the first input of the `Evaluate Model` module

    ![Image shows the steps to add and configure the Evaluate Model module.](images/18.png 'Evaluate Model')

# Exercise 3: Submit Training Pipeline

## Task 1: Create Experiment and Submit Pipeline

1. Select **Submit** to open the `Setup pipeline run` editor.

    ![Image shows where to select the submit button to open the setup pipeline run editor.](images/19.png 'Submit Pipeline')

    > Please note that the button name in the UI is changed from **Run** to **Submit**.

2. In the `Setup pipeline run editor`, select **Experiment, Create new** and provide `New experiment name:` **designer-run**, and then select **Submit**.

    ![Image shows how to provide the experiment name in the setup pipeline run editor and start the pipeline run.](images/20.png 'Submit Pipeline')

3. Wait for pipeline run to complete. It will take around **8 minutes** to complete the run.

4. While you wait for the model training to complete, you can learn more about the training algorithm used in this lab by selecting [Linear Regression module](https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/linear-regression).

# Exercise 4: Visualize Training Results

## Task 1: Visualize the Model Predictions

1. Select **Score Model, Outputs, Visualize** to open the `Score Model result visualization` dialog.

    ![Image shows how to open the score model result visualization dialog.](images/21.png 'Score Model Results')

2. Observe the predicted values under the column **Scored Labels**. You can compare the predicted values (`Scored Labels`) with actual values (`totalAmount`).

    ![Image shows the score model result visualization dialog.](images/22.png 'Model Predictions')

## Task 2: Visualize the Evaluation Results

1. Select **Evaluate Model, Outputs, Visualize** to open the `Evaluate Model result visualization` dialog.

    ![Image shows how to open the evaluate model result visualization dialog.](images/23.png 'Evaluate Model Results')

2. Evaluate the model performance by reviewing the various evaluation metrics, such as **Mean Absolute Error**, **Root Mean Squared Error**, etc.

    ![Image shows the evaluate model result visualization dialog.](images/24.png 'Evaluation Metrics')

# Next Steps
Congratulations! You have trained and evaluated your first machine learning model. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.
