# Exercise 6: Realtime Inference Pipeline

## Task 1: Create Pipeline

1. Select **Create inference pipeline, Real-time inference pipeline** to create a new inference pipeline.

    ![Image shows how to create a new real-time inference pipeline.](images/25.png 'Create Real-time Inference Pipeline')

## Task 2: Run Pipeline

1. Select **Run** to open the `Set up pipeline run` editor.

    ![Select run to open the set up pipeline run editor.](images/26.png 'Real-time Inference Pipeline')

2. Select **Experiment** from the list: **designer-run**, and then select **Run**.

    ![Image shows how to select the experiment name in the set up pipeline run editor and start the pipeline run.](images/27.png 'Setup Pipeline Run')

3. Wait for pipeline run to complete. It will take around **7 minutes** to complete the run.

# Exercise 7: Deploy Web Service on Kubernetes Service Compute

## Task 1: Deploy Web Service

1. After the inference pipeline run is finished, select **Deploy** to open the `Set up real-time endpoint` editor.

    ![Select deploy to open the set up real-time endpoint editor.](images/28.png 'Deploy')

2. In the `Set up real-time endpoint` editor, provide the following information and then select **Deploy**.

    1. Real-time endpoint name: **nyc-taxi-fare-predictor**

    2. Select an existing compute target name: **nyc-taxi-service**

    ![Image shows the information provided in the set up real-time endpoint editor.](images/29.png 'Deploy Web Service')

*Note that **nyc-taxi-service** is the Kubernetes Service Compute created in the prerequisites section*

3. Wait for the deployment to complete. The status of the deployment can be observed above the `Pipeline Authoring Editor`.

    ![Image highlights the region where you see the status of the web service deployment.](images/30.png 'Successful Deployment')

## Task 2: Review Deployed Web Service

1. To view the deployed web service, select the **Endpoints** section in your Azure Portal Workspace.

2. Select the deployed web service: **nyc-taxi-fare-predictor** to open the deployment details page.

    ![Image highlights the deployed web service, nyc-taxi-fare-predictor.](images/31.png 'Endpoints')

*Note: you have to select the text of the service name to open the deployment details page*

## Task 3: Review how to Consume the Deployed Web Service

1. Select **Consume** tab, to observe the following information:

    1. `Basic consumption info` displays the **REST endpoint**, **Primary key**, and **Secondary key**.

    2. `Consumption option` shows code samples in **C#**, **Python**, and **R** on how to call the endpoint to consume the webservice.

    ![Image highlights the two key regions in the consume tab of the deployment details, the first region shows basic consumption information, and the second region shows code samples of how to consume the deployed service.](images/32.png 'Consume')

# Exercise 8: Challenge Experiment

Is there another regression model that can give us an improved evaluation score on the `Root Mean Square Error (RMSE)` metric?  The `Boosted Decision Tree Regression` gave us an RMSE score of **3.92**. Experiment with other models like the `Neural Net Regression` model and evaluate if you can train a better performing model on the RMSE metric. Please note that the objective is to minimize the RMSE score.

# Exercise 9: Cleanup Resources

## Task 1: Delete Web Service

1. Select the **Endpoints** section in your Azure Portal Workspace.

2. Select **nyc-taxi-fare-predictor, Delete** to delete the web service.

    ![Image shows how to delete the web service, nyc-taxi-fare-predictor.](images/33.png 'Endpoints')

## Task 2: Delete Training Cluster

1. Select the **Compute, Training Clusters** section in your Azure Portal Workspace.

2. Select **qs-compute, Delete** to delete the training cluster.

    ![Image shows how to delete the training cluster, qs-compute.](images/34.png 'Training Clusters')

## Task 3: Delete Inference Cluster

1. Select the **Compute, Inference Clusters** section in your Azure Portal Workspace.

2. Select **nyc-taxi-service, Delete** to delete the inference cluster.

    ![Image shows how to delete the inference cluster, nyc-taxi-service.](images/35.png 'Inference Clusters')
