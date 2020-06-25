# Lab Overview

[Azure Machine Learning designer](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-designer) (preview) gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning designer also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications.

In this lab, we will be compare the performance of two regression algorithms: `Boosted Decision Tree Regression` and `Neural Net Regression` for predicting automobile prices. We will do all of this from the Azure Machine Learning designer without writing a single line of code.

# Exercise 1: Create Training Pipeline

## Task 1: Open Sample 2: Regression - Automobile Price Prediction (Compare algorithms)

1. In [Azure portal](https://portal.azure.com/), open the available machine learning workspace.

2. Select **Launch now** under the **Try the new Azure Machine Learning studio** message.

    ![Launch Azure Machine Learning studio.](images/01a.png 'Launch AML')

3. When you first launch the studio, you may need to set the directory and subscription. If so, you will see this screen:

    ![Launch Azure Machine Learning studio.](images/00.png 'Launch AML')

    > For the directory, select **Udacity** and for the subscription, select **Azure Sponsorship**. For the machine learning workspace, you may see multiple options listed. **Select any of these** (it doesn't matter which) and then click **Get started**.

4. From the studio, select **Designer, Sample 2: Regression - Automobile Price Prediction (Compare algorithms)**.

   ![Image highlights the steps to open the sample pipeline, Sample 2: Regression - Automobile Price Prediction (Compare algorithms).](images/01.png 'Pipeline Authoring Editor')

## Task 2: Setup Compute Target

1. In the settings panel on the right, select **Select compute target**.

    ![Image highlights the link to select to open the setup compute target editor.](images/02.png 'Setup Compute Target')

2. In the `Set up compute target` editor, select the available compute, and then select **Save**.
```

NOTE : If you are facing any difficulties in accessing any of the pop-up windows or any of the buttons properly, Please refer to the Help section in the lab environment
```

   ![Image shows how to select the existing compute target named qs-compute.](images/03.png 'Setup Compute Target')

## Task 3: Delete Pipeline Modules

1. From the `right-hand-side` of the pipeline, select the **Decision Forest Regression module** and then select the **Delete Icon**.

    ![Image shows how to delete an existing module.](images/04.png 'Delete Module')

## Task 4: Setup the Neural Net Regression Module

1. Select **Machine Learning Algorithms** section in the left navigation. Follow the steps outlined below:

    1. Select the **Neural Net Regression** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Set `Number of hidden nodes` to **1000**

    4. Set `Learning rate` to **0.0001**

    5. Set `Number of learning iterations` to **10000**

    6. Set `Random number seed` to **139**

    7. Connect the `Neural Net Regression` module to the first input of the `Train Model` module

    ![Image shows the steps to add and configure the Neural Net Regression module.](images/06.png 'Neural Net Regression Module')

# Exercise 2: Submit Training Pipeline

## Task 1: Create Experiment and Submit Pipeline

1. Select **Submit** to open the `Setup pipeline run` editor.

    ![Image shows where to select the submit button to open the setup pipeline run editor.](images/07.png 'Submit Pipeline')

    > Please note that the button name in the UI is changed from **Run** to **Submit**.

2. In the `Setup pipeline run editor`, select **Experiment, Create new** and provide `New experiment name:` **automobile-price-prediction**, and then select **Submit**.

    ![Image shows how to provide the experiment name in the setup pipeline run editor and start the pipeline run.](images/08.png 'Submit Pipeline')

3. Wait for pipeline run to complete. It will take around **10 minutes** to complete the run.

4. While you wait for the model training to complete, you can learn more about the evaluation metrics for the regression algorithm used in this lab by selecting [Metrics for regression models](https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/evaluate-model#bkmk_regression).

# Exercise 3: Compare Model Performance

## Task 1: Open Evaluation Results

1. Select **Evaluate Model, Outputs, Visualize** to open the `Evaluate Model result visualization` dialog.

    ![Image shows how to open the evaluate model result visualization dialog.](images/09.png 'Evaluate Model Results')

## Task 2: Compare Performance Metrics

1. Select the regression performance metric **Root_Mean_Squared_Error** and compare performance of the two algorithms: `Boosted Decision Tree Regression` and `Neural Net Regression`. Note that smaller value for `Root_Mean_Squared_Error` implies better performance.

    ![Image shows the evaluate model result visualization dialog.](images/10.png 'Compare Performance Metrics')

## Task 3: Conclusion

1. Based on the performance metric, `Root_Mean_Squared_Error`, it shows that the `Boosted Decision Tree Regression` algorithm outperforms the `Neural Net Regression` algorithm. One recommendation for next steps is to tune the hyperparameters for the `Neural Net Regression` module to see if we can improve its performance.

# Next Steps
Congratulations! You have trained and compared performance of two different regression machine learning models. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.
