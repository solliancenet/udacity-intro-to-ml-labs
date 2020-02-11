# Lab Overview

Azure Machine Learning service fully supports open-source technologies. So you can use tens of thousands of open-source Python packages with machine learning components. Examples are PyTorch, TensorFlow, and scikit-learn. Support for rich tools makes it easy to interactively explore and prepare data and then develop and test models. Examples are [Jupyter notebooks](https://jupyter.org) or the [Azure Machine Learning for Visual Studio Code](https://marketplace.visualstudio.com/items/itemName/ms-toolsai.vscode-ai/overview) extension.

By using Azure Machine Learning service, you can start training on your local machine and then scale out to the cloud. With many available [compute targets](https://docs.microsoft.com%/en-us/azure/machine-learning/service/how-to-set-up-training-targets), like Azure Machine Learning Compute and [Azure Databricks](https://docs.microsoft.com/en-us/azure/azure-databricks/what-is-azure-databricks), and with [advanced hyperparameter tuning services](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-tune-hyperparameters), you can build better models faster by using the power of the cloud. When you have the right model, you can easily deploy it in a container such as Docker. So it's simple to deploy to Azure Container Instances or Azure Kubernetes Service. Or you can use the container in your own deployments, either on-premises or in the cloud. For more information, see the article on [how to deploy and where](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-deploy-and-where).

You can manage the deployed models and track multiple runs as you experiment to find the best solution. After it's deployed, your model can return predictions in [real time](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-consume-web-service) or [asynchronously](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-run-batch-predictions) on large quantities of data. And with advanced [machine learning pipelines](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-ml-pipelines), you can collaborate on all the steps of data preparation, model training and evaluation, and deployment.

In this experience you will learn how the automated machine learning capability in Azure Machine Learning (AML) can be used for the life cycle management of the manufactured vehicles and how AML helps in creation of better vehicle maintenance plans. To accomplish this, you will train a Linear Regression model to predict the number of days until battery failure using Automated Machine Learning in Jupyter Notebooks.

## Exercise 1: Creating a model using automated machine learning

In this exercise, you will create a model that predicts battery failure from time-series data using the visual interface to automated machine learning in an Azure Machine Learning workspace.

### Task 1: Create an automated machine learning experiment using the Portal

1. Navigate to your Azure Machine Learning workspace in the Azure Portal. Select **Launch now** under the **Try the new Azure Machine Learning studio** message. Alternatively, you can navigate directly to the new [Azure Machine Learning studio](https://ml.azure.com/). This will prompt you to select the workspace as part of the sign-in process.

   ![Navigate to Azure Machine Learning studio](./images/01.png)

2. Select **Automated ML** in the left navigation bar.

   ![Select Automated ML](./images/002_AutomatedML.png)

3. Select **New automated ML run** to start creating a new experiment.

   ![New automated ML run](./images/003_CreateAutomatedMLRun.png)

4. Select **Create dataset** and choose the **From web files** option from the drop-down.

   ![Create dataset from local file](./images/004_NewDataset_FromURL.png)

5. Fill in the training data URL in the `Web URL` field: `https://introtomlsampledata.blob.core.windows.net/data/battery-lifetime/training-formatted.csv`, make sure the name is set to `training-formatted-dataset`, and select **Next** to load a preview of the parsed training data.

   ![Training data web URL](./images/005_Dataset_BasicInfo.png)

6. In the `Settings and preview` page, scroll to the right to observe all of the columns in the data.

   ![Reviewing the training data](./images/006_ReviewDataFile.png)

7. Select **Next** to check the schema and then confirm the dataset details by selecting **Next** and then **Create** on the confirmation page.

   ![Reviewing the schema of training data](./images/007_TrainingDataSchema.png)

   ![Confirm dataset creation](./images/007_ConfirmDataset.png)

8. Now you should be able to select the newly created dataset for your experiment. Select the `training-formatted-dataset` dataset and select **Next** to move to the experiment run details page.

   ![Select the dataset](./images/008_SelectDataset.png)

9. You will now configure the Auto ML run basic settings by providing the following values for the experiment name, target column and training compute:

   - Experiment name: **automl-regression**
   - Target column: select **Survival_In_Days**
   - Select training compute target: : select **aml-compute-cpu**

   ![Setup Auto ML experiment basic settings](./images/009_SetupExperiment.png)

10. Select **Next** and select **Regression** in the `Task type and settings` page.

    ![Select Regression task type](./images/010_TaskTypeForExperiment.png)

11. Select **View additional configuration settings** to open the advanced settings section. Provide the following settings:

    - Primary metric: **Normalized root mean squared error**
    - Exit criterion > Metric score threshold: **0.09**
    - Validation > Validation type: **k-fold cross validation**
    - Validation > Number of Cross Validations: **5**
    - Concurrency > Max concurrent iterations: **1**

    ![Configuring the Advanced Settings as described](./images/011_TaskConfigurationSettings.png)

12. Select **Save** and then **Finish** to begin the automated machine learning process.

    ![Start Automate ML run](./images/012_CreatingExperiment.png)

13. Wait until the `Run status` becomes **Running** in the `Run Detail page`.

    ![Preparing experiment](./images/012_PreparingExperiment.png)

### Task 2: Review the experiment run results

1. The experiment will run for about _15 minutes_. While it runs and once it completes, you should check the `Models` tab on the `Run Detail` page to observe the model performance for the primary metric for different runs.

   ![Review run details - graph view](./images/021_RunDetails1.png)

2. In the models list, notice at the top the iteration with the best **normalized root mean square error** score. Note that the normalized root mean square error measures the error between the predicted value and actual value. In this case, the model with the lowest normalized root mean square error is the best model.

   ![Review run details - table view](./images/022_RunDetails2.png)

3. Select **Experiments** on the left navigation pane and select the experiment `automl-regression` to see the list of available runs.

   ![Open experiment runs table](./images/023_CheckExperimentRuns.png)

4. Select the option to **Include child runs** to be able to examine  model performance for the primary metric of different runs. By default, the left chart describes the `mean_absolute_error` value for each run. Select the pen icon on the right corner of the `mean_absolute_error` chart to configure the `normalized_root_mean_square_error` metric representation.

   ![Review runs - chart view](./images/024_IncludeChildRuns.png)

# Next Steps

Congratulations! You have trained a simple recommender. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.