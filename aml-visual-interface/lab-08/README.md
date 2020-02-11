# Lab Overview

[Azure Machine Learning designer](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-designer) (preview) gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning designer also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications.

In this lab, we will be compare the performance of two binary classifiers: Two-Class Boosted Decision Tree and Two-Class Logistic Regression for predicting customer churn. The goal is to run an expensive marketing campaign for high risk customers; thus, the **precision** metric is going to be key in evaluating performance of these two algorithms. We will do all of this from the Azure Machine Learning designer without writing a single line of code.

# Exercise 1: Create Training Pipeline

## Task 1: Open Sample 5: Binary Classification – Customer Relationship Prediction

1. From the studio, select **Designer, Sample 5: Binary Classification – Customer Relationship Prediction**.

   ![Image highlights the steps to open the sample pipeline, Sample 5: Binary Classification – Customer Relationship Prediction.](images/01.png 'Pipeline Authoring Editor')

## Task 2: Setup Compute Target

1. In the settings panel on the right, select **Select compute target**.

    ![Image highlights the link to select to open the setup compute target editor.](images/02.png 'Setup Compute Target')

2. In the `Set up compute target` editor, select the available compute, and then select **Save**.

    ![Image shows how to select the existing compute target named qs-compute.](images/03.png 'Setup Compute Target')

## Task 3: Delete Pipeline Modules

1. From the `right-hand-side` of the pipeline, select the **Two-Class Boosted Decision Tree module** and then select the **Delete Icon**.

    ![Image shows how to delete an existing module.](images/04.png 'Delete Module')

2. From the `right-hand-side` of the pipeline, select the **SMOTE module** and then select the **Delete Icon**.

    ![Image shows how to delete an existing module.](images/05.png 'Delete Module')

## Task 4: Setup the Two-Class Logistic Regression Module

1. Select **Machine Learning Algorithms** section in the left navigation. Follow the steps outlined below:

    1. Select the **Two-Class Logistic Regression** prebuilt module

    2. Drag and drop the selected module on to the canvas

    3. Connect the `Two-Class Logistic Regression` module to the first input of the `Train Model` module

    4. Connect the first output of the `Split Data` module to the second input of the `Train Model` module

    ![Image shows the steps to add and configure the Two-Class Logistic Regression module.](images/06.png 'Two-Class Logistic Regression Module')

# Exercise 2: Run Training Pipeline

## Task 1: Create Experiment and Run Pipeline

1. Select **Run** to open the `Setup pipeline run` editor.

    ![Image shows where to select the run button to open the setup pipeline run editor.](images/07.png 'Run Pipeline')

2. In the `Setup pipeline run` editor, select **+New experiment**, provide `Experiment Name:` **Churn-Predictor**, and then select **Run**.

    ![Image shows how to provide the experiment name in the setup pipeline run editor and start the pipeline run.](images/08.png 'Run Pipeline')

3. Wait for pipeline run to complete. It will take around **5 minutes** to complete the run.

4. While you wait for the model training to complete, you can learn more about the evaluation metrics for the classification algorithm used in this lab by selecting [Metrics for classification models](https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-module-reference/evaluate-model#bkmk_classification).

# Exercise 3: Compare Model Performance

## Task 1: Open Evaluation Results for Two-Class Boosted Decision Tree

1. From the `left-hand-side` of the pipeline, select **Evaluate Model, Outputs, Visualize** to open the `Evaluate Model result visualization` dialog for the `Two-Class Boosted Decision Tree` module.

    ![Image shows how to open the evaluate model result visualization dialog.](images/09.png 'Evaluate Model Results')

## Task 2: Evaluate Two-Class Boosted Decision Tree Performance

1. Scroll down to review model performance metrics for `Two-Class Boosted Decision Tree`. Observe that the **Precision** value is around **0.7**.

    ![Image shows the evaluate model result visualization dialog for Two-Class Boosted Decision Tree.](images/10.png 'Two-Class Boosted Decision Tree Performance')

## Task 3: Open Evaluation Results for Two-Class Logistic Regression

1. From the `right-hand-side` of the pipeline, select **Evaluate Model, Outputs, Visualize** to open the `Evaluate Model result visualization` dialog for the `Two-Class Logistic Regression` module.

    ![Image shows how to open the evaluate model result visualization dialog.](images/11.png 'Evaluate Model Results')

## Task 4: Evaluate Two-Class Logistic Regression Performance

1. Scroll down to review model performance metrics for `Two-Class Logistic Regression`. Observe that the **Precision** value is around **0.3**.

    ![Image shows the evaluate model result visualization dialog for Two-Class Logistic Regression.](images/12.png 'Two-Class Logistic Regression Performance')

## Task 5: Conclusion

1. Based on the primary performance metric, `Precision`, it shows that the `Two-Class Boosted Decision Tree` algorithm outperforms the `Two-Class Logistic Regression` algorithm.

# Next Steps
Congratulations! You have trained and compared performance of two different classification machine learning models. You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.
