# Train a simple neural net model

Although neural networks are widely known for use in deep learning and modeling complex problems such as image recognition, they are easily adapted to regression problems. Any class of statistical models can be termed a neural network if they use adaptive weights and can approximate non-linear functions of their inputs. Thus neural network regression is suited to problems where a more traditional regression model cannot fit a solution.

Neural network regression is a supervised learning method, and therefore requires a tagged dataset, which includes a label column. Because a regression model predicts a numerical value, the label column must be a numerical data type.

## Lab Overview

In this lab we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. Based on the enriched dataset, we will configure the prebuilt Neural Network Regression module to create a regression model using a customizable neural network algorithm. We will train the model by providing the model and the NYC taxi dataset as an input to Train Model. The trained model can then be used to predict NYC taxi fares. We will do all of this from the Azure Machine Learning designer without writing a single line of code.

# Exercise 1: Register Dataset with Azure Machine Learning studio

## Task 1: Upload Dataset

1. From the studio, select **Datasets, + Create dataset, From web files**. This will open the `Create dataset from web files` dialog on the right.

   ![Image highlights the steps to open the create dataset from web files dialog.](images/01.png 'Create dataset from web files')

2. In the Web URL field provide the following URL for the training data file:
    ```
    https://introtomlsampledata.blob.core.windows.net/data/nyc-taxi/nyc-taxi-sample-data.csv
    ```
3. Provide `nyc-taxi-sample-data` as the Name, leave the remaining values at their defaults and select **Next**.

    ![Upload nyc-taxi-sample-data.csv from a URL.](images/02.png 'Upload dataset')

## Task 2: Preview Dataset

1. On the Settings and preview panel, set the column headers drop down to `All files have same headers`.

2. Scroll the data preview to right to observe the target column: `totalAmount`. After you are done reviewing the data, select **Next**

    ![Scroll right to review dataset.](images/03.png 'Review dataset')

## Task 3: Select Columns

1. Select columns from the dataset to include as part of your training data. Leave the default selections and select **Next**

    ![Select columns from the dataset to include as part of your training data.](images/04.png 'Select columns')

## Task 4: Create Dataset

1. Confirm the dataset details and select **Create**

    ![Confirm the details of the dataset you uploaded and then select Create.](images/05.png 'Confirm and create the dataset')

# Exercise 2: Create New Training Pipeline

## Task 1: Open Pipeline Authoring Editor

1. From the studio, select **Designer, +**. This will open a `visual pipeline authoring editor`.

   ![Image highlights the steps to open the pipeline authoring editor.](images/06.png 'Pipeline Authoring Editor')

## Task 2: Setup Compute Target

1. In the settings panel on the right, select **Select compute target**.

    ![Image highlights the link to select to open the setup compute target editor.](images/07.png 'Setup Compute Target')

2. In the `Set up compute target` editor, select the available compute, and then select **Save**.

    ![Image shows how to select an existing compute target .](images/08.png 'Setup Compute Target')

## Task 3: Add Dataset

1. Select **Datasets** section in the left navigation. Next, select **My Datasets, nyc-taxi-sample-data** and drag and drop the selected dataset on to the canvas.

    ![Image shows the dataset, nyc-taxi-sample-data, added to the canvas.](images/09.png 'Add Dataset')

## Task 4: Split Dataset

1. Select **Data Transformation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Split Data** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Fraction of rows in the first output dataset: **0.7**

    4. Connect the `Dataset` to the `Split Data` module

    ![Image shows the steps to add and configure the Split Data module.](images/10.png 'Split Data Module')

*Note that you can run the pipeline at any point to peek at the outputs and activities. Running pipeline also generates metadata that is available for downstream activities such selecting column names from a list in selection dialogs.*

## Task 5: Initialize Regression Model

1. Select **Machine Learning Algorithms** section in the left navigation. Follow the steps outlined below:

    1. Select the **Neural Network Regression** prebuilt module, in the Regression category.

    2. Drag and drop the selected module on to the canvas

    3. Create trainer mode: **Single Parameter**. This option indicates how you want the model to be trained.

    4. Hidden layer specification: **Fully connected case**. 
    5. For Learning rate: **0.001**.
    
    ![Image shows the steps to add and configure the Neural Network Regression module.](images/13.png 'Neural Network Regression')

    *Note: Because the number of nodes in the input layer is determined by the number of features in the training data, in a regression model there can be only one node in the output layer.*


## Task 6: Setup Train Model Module

1. Select **Model Training** section in the left navigation. Follow the steps outlined below:

    1. Select the **Train Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Neural Network Regression` module to the first input of the `Train Model` module

    4. Connect the first output of the `Split Data` module to the second input of the `Train Model` module

    5. Select the **Edit column** link to open the `Label column` editor

    ![Image shows the steps to add and configure the Train Model module.](images/14.png 'Train Model Module')

2. The `Label column` editor allows you to specify your `Label or Target column`. Type in the label column name **totalAmount** and then select **Save**.

    ![Image shows the label column editor and how to provide the label column name.](images/15.png 'Label Column')

## Task 7: Setup Score Model Module

1. Select **Model Scoring & Evaluation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Score Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Train Model` module to the first input of the `Score Model` module

    4. Connect the second output of the `Split Data` module to the second input of the `Score Model` module

    ![Image shows the steps to add and configure the Score Model module.](images/16.png 'Score Model')

*Note that `Split Data` module will feed data for both model training and model scoring. The first output (0.7 fraction) will connect with the `Train Model` module and the second output (0.3 fraction) will connect with the `Score Model` module.*

## Task 8: Setup Evaluate Model Module

1. Select **Model Scoring & Evaluation** section in the left navigation. Follow the steps outlined below:

    1. Select the **Evaluate Model** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Score Model` module to the first input of the `Evaluate Model` module

    ![Image shows the steps to add and configure the Evaluate Model module.](images/17.png 'Evaluate Model')

# Exercise 3: Run Training Pipeline

## Task 1: Create Experiment and Run Pipeline

1. Select **Run** to open the `Setup pipeline run` editor.

    ![Image shows where to select the run button to open the setup pipeline run editor.](images/18.png 'Run Pipeline')

2. In the `Setup pipeline run` editor, select **+New experiment**, provide `Experiment Name:` **neural-network-regression**, and then select **Run**.

    ![Image shows how to provide the experiment name in the setup pipeline run editor and start the pipeline run.](images/19.png 'Run Pipeline')

3. Wait for pipeline run to complete. It will take around **8 minutes** to complete the run.

4. While you wait for the model training to complete, you can learn more about the training algorithm used in this lab by selecting [Neural Network Regression module](https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/neural-network-regression).

# Exercise 4: Visualize Training Results

## Task 1: Visualize the Model Predictions

1. Select **Score Model, Outputs, Visualize** to open the `Score Model result visualization` dialog or just simply right-click the `Score Model` module and select **Visualize Scored Dataset**.

    ![Image shows how to open the score model result visualization dialog.](images/20.png 'Score Model Results')

2. Observe the predicted values under the column **Scored Labels**. You can compare the predicted values (`Scored Labels`) with actual values (`totalAmount`).

    ![Image shows the score model result visualization dialog.](images/21.png 'Model Predictions')

## Task 2: Visualize the Evaluation Results

1. Select **Evaluate Model, Outputs, Visualize** to open the `Evaluate Model result visualization` dialog or just simply right-click the `Evaluate Model` module and select **Visualize Evaluation Results**.

    ![Image shows how to open the evaluate model result visualization dialog.](images/22.png 'Evaluate Model Results')

2. Evaluate the model performance by reviewing the various evaluation metrics, such as **Mean Absolute Error**, **Root Mean Squared Error**, etc.

    ![Image shows the evaluate model result visualization dialog.](images/23.png 'Evaluation Metrics')

# Next Steps

Congratulations! You have trained a simple neural net model using the prebuilt Neural Network Regression module in the AML visual designer. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.