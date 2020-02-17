# Compute Resources

## Deploy a trained model as a webservice

In previous lessons, we spent much time talking about training a machine learning model, which is a multi-step process involving data preparation, feature engineering, training, evaluation, and model selection. The model training process can be very compute-intensive, with training times spanning across many hours, days, or weeks depending on the amount of data, type of algorithm used, and other factors. A trained model, on the other hand, is used to make decisions on new data quickly. In other words, it infers things about new data it is given based on its training. Making these decisions on new data on-demand is called real-time inferencing.

# Overview

In this lab, you learn how to deploy a trained model that can be used as a webservice, hosted on an Azure Kubernetes Service (AKS) cluster. This process is what enables you to use your model for real-time inferencing.

The Azure Machine Learning designer simplifies the process by enabling you to train and deploy your model without writing any code. 

## Exercise 1: Open a sample training pipeline

### Task 1: Open the pipeline authoring editor

1. Within Azure Machine Learning Studio, select **Designer** in the left-hand menu. Next, select **Sample 1: Regression - Automobile Price Prediction (Basic)** under the **New pipeline** section. This will open a `visual pipeline authoring editor`.

   ![The Sample 1 pipeline is selected.](images/new-pipeline.png "Designer: New pipeline")

### Task 2: Setup the compute target

1. In the settings panel on the right, select **Select compute target**.

   ![The select compute target link is highlighted.](images/select-compute-target-link.png "Select compute target link")

2. In the `Set up compute target` editor, select the existing compute target, then select **Save**.

   ![Select the existing compute target, then select Save.](images/set-up-compute-target.png "Set up compute target")

### Task 3: Create a new experiment and run the pipeline

1. Select **Run** to open the `Set up pipline run` editor.

   ![The Run button is highlighted.](images/run-button.png "Run")

2. In the `Set up pipeline run` editor, select **+ New experiment**, provide a unique **Experiment Name**, and then select **Run**.

   ![The dialog is displayed with the previously described values.](images/set-up-pipeline-run.png "Set up pipeline run")

3. Wait for the pipeline run to complete. It will take around **10 minutes** to complete the run.

## Exercise 2: Real-time inference pipeline

### Task 1: Create pipeline

1. Select **Create inference pipeline**, then select **Real-time inference pipeline** from the list to create a new inference pipeline.

   ![Select the real-time inference pipeline option.](images/new-real-time-inference-pipeline.png "Real-time inference pipeline")

### Task 2: Run the pipeline

1. Select **Run** to open the `Set up pipeline run` editor.

   ![Select the Run button.](images/run-inference-pipeline.png "Run")

2. Select **Experiment**, then select the experiment you created in an earlier step. Select **Run** to start the pipeline.

   ![Select your previous experiment.](images/set-up-inference-pipeline-run.png "Set up pipeline run")

3. Wait for pipeline run to complete. It will take around **7 minutes** to complete the run.

## Exercise 3: Deploy web service on Azure Kubernetes Service compute

### Task 1: Deploy the web service

1. After the inference pipeline run is finished, select **Deploy** to open the `Set up real-time endpoint` editor.

   ![Select Deploy to open the editor.](images/deploy-web-service.png "Deploy")

2. In the `Set up real-time endpoint` editor, select your **existing compute target**, then select **Deploy**.

   ![The dialog shows the selected compute target.](images/set-up-real-time-endpoint.png "Set up real-time endpoint")

3. Wait for the deployment to complete. The status of the deployment can be observed above the `Pipeline Authoring Editor`.

   ![Deployment completed dialog is shown.](images/deploy-succeeded.png "Deploy - Succeeded")

### Task 2: Review deployed web service

1. To view the deployed web service, select the **Endpoints** section in your Azure Portal Workspace.

2. Select the deployed web service: **sample-1-regression---automobile** to open the deployment details page.

   ![The deployed service is highlighted within the Endpoints blade.](images/endpoints.png "Endpoints")

   *Note: you have to select the text of the service name to open the deployment details page*

### Task 3: Review how to consume the deployed web service

1. Select the **Consume** tab to observe the following information:

   1. `Basic consumption info` displays the **REST endpoint**, **Primary key**, and **Secondary key**.

   2. `Consumption option` shows code samples in **C#**, **Python**, and **R** on how to call the endpoint to consume the webservice.

   ![The Consume tab is displayed.](images/consume.png "Service details: Consume")

# Next Steps

Congratulations! You have just learned how to train and deploy a model to an Azure Kubernetes Service (AKS) cluster for real-time inferencing. You can now return to the Udacity portal to continue with the lesson.

