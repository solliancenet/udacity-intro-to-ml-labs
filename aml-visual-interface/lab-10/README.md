# Lab Overview

Automated machine learning picks an algorithm and hyperparameters for you and generates a model ready for deployment. There are several options that you can use to configure automated machine learning experiments.

Configuration options available in automated machine learning:

- Select your experiment type: Classification, Regression or Time Series Forecasting
- Data source, formats, and fetch data
- Choose your compute target
- Automated machine learning experiment settings
- Run an automated machine learning experiment
- Explore model metrics
- Register and deploy model

You can create and run automated machine learning experiments in code using the [Azure ML Python SDK](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-configure-auto-train) or if you prefer a no code experience, you can also create your automated machine learning experiments in [Azure Machine Learning Studio](https://ml.azure.com/).

In this lab, we will use Automated Machine Learning to find the best performing binary classification model for predicting customer churn. We will do all of this from the [Azure Machine Learning Studio](https://ml.azure.com/) without writing a single line of code.

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
    https://introtomlsampledata.blob.core.windows.net/data/crm-churn/crm-churn.csv
    ```

6. Provide `CRM-Churn` as the Name, leave the remaining values at their defaults and select **Next**.

    ![Upload crm-churn.csv from a URL.](images/05.png 'Upload dataset')

## Task 2: Preview Dataset

1. On the Settings and preview panel, set the column headers drop down to `All files have same headers`.

2. Review the dataset and then select **Next**

    ![Scroll right to review dataset.](images/06.png 'Review dataset')

## Task 3: Select Columns

1. Keep the default selections, and select **Next**

    ![Select columns from the dataset to include as part of your training data.](images/07.png 'Select columns')

## Task 4: Create Dataset

1. Confirm the dataset details and select **Create**

    ![Confirm the details of the dataset you uploaded and then select Create.](images/08.png 'Confirm and create the dataset')

# Exercise 2: Setup New Automated Machine Learning Experiment

## Task 1: Create New Automated Machine Learning Experiment

1. From the studio home, select **Create new, Automated ML run**

    ![Create new Automated ML run from Azure Machine Learning studio.](images/02.png 'New Automated ML run')

2. This will open a `Create a new automated machine learning experiment` page

## Task 2: Select Training Data

1. Select the dataset `CRM-Churn` and then select **Next**

    ![Select the dataset CRM-Churn and then select Next.](images/09.png 'Select dataset')

## Task 3: Create a new Automated ML run

1. Provide an experiment name: **Churn-Predictor**

2. Select target column: **Col1**

3. Select compute target: **select the available compute**

4. Select **Next**

    ![Configure a new Automated ML run.](images/10.png 'Configure Run')

## Task 4: Setup Task type and Settings

1. Select task type: **Classification**, and then select **View additional configuration settings**

    ![Select task type, classification.](images/11.png 'Select task type')

2. This will open the `Additional configurations` dialog.

3. Provide the following information and then select **Save**

   1. Primary metric: **AUC weighted**
   2. Exit criteria, Metric score threshold: `0.707`

   ![Setup additional configurations.](images/12.png 'Additional configurations')

   *Note that we are setting a metric score threshold to limit the training time. In practice, for initial experiments, you will typically only set the training job time to allow AutoML to discover the best algorithm to use for your specific data.*

# Exercise 3: Start and Monitor Experiment

## Task 1: Start Experiment

1. Select **Finish** to start running the experiment

    ![Select Finish to start running the experiment.](images/13.png 'Start Experiment')

## Task 2: Monitor Experiment

1. The experiment will run for about *5 min*

2. In the **Details** tab, observe the **run status** of the job.

    ![Run Details tab showing run status.](images/14.png 'Run Details')

3. Wait till the run status becomes **Completed**.

    ![Run Details tab showing run status.](images/16.png 'Run Details')

4. While you wait for the model training to complete, you can learn to view and understand the charts and metrics for your automated machine learning run by selecting [Understand automated machine learning classification results](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-understand-automated-ml#classification).

# Exercise 4: Review Best Model's Performance

## Task 1: Review Best Model Performance

1. From the `Details` tab review the best model's `Algorithm name` and its corresponding `AUC weighted` score. Next, select the best model's **Algorithm name**

    ![Run Details tab showing recommended model.](images/17.png 'Recommended Model')

2. Select **View all other metrics** to review the various `Run Metrics` to evaluate the model performance. Next, select **Metrics**

    ![Model Details tab showing model performance metrics.](images/18.png 'Model details')

3. Select **accuracy_table, Chart** to review the various model performance curves, such as Precision-Recall, ROC, Calibration curve, and Gain & Lift curves.

    ![Model Visualizations tab showing model performance curves.](images/19.png 'Model Performance')

# Next Steps

Congratulations! You have trained and evaluated a binary classification model using automated machine learning. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.
