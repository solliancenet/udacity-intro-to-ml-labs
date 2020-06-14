# Explaining models

## Model interpretability with Azure Machine Learning service
Machine learning interpretability is important in two phases of machine learning development cycle:

* During training: Model designers and evaluators require interpretability tools to explain the output of a model to stakeholders to build trust. They also need insights into the model so that they can debug the model and make decisions on whether the behavior matches their objectives. Finally, they need to ensure that the model is not biased.
* During inferencing: Predictions need to be explainable to the people who use your model. For example, why did the model deny a mortgage loan, or predict that an investment portfolio carries a higher risk?

The [Azure Machine Learning Interpretability Python SDK](https://docs.microsoft.com/en-us/python/api/azureml-explain-model/?view=azure-ml-py) incorporates technologies developed by Microsoft and proven third-party libraries (for example, SHAP and LIME). The SDK creates a common API across the integrated libraries and integrates Azure Machine Learning services. Using this SDK, you can explain machine learning models globally on all data, or locally on a specific data point using the state-of-art technologies in an easy-to-use and scalable fashion.

# Overview
In this lab, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. We will use data transformations and the GradientBoostingRegressor algorithm from the scikit-learn library to train a regression model to predict taxi fares in New York City based on input features such as, number of passengers, trip distance, datetime, holiday information and weather information.

The primary goal of this quickstart is to explain the predictions made by our trained model with the various [Azure Model Interpretability](https://docs.microsoft.com/en-us/azure/machine-learning/service/machine-learning-interpretability-explainability) packages of the Azure Machine Learning Python SDK.

## Exercise 1: Run the Notebook for this Lab

1. Download the notebook on your local disk from the following URL:

    `https://github.com/solliancenet/udacity-intro-to-ml-labs/blob/master/aml-visual-interface/lab-23/notebook/interpretability-with-AML.ipynb`

   Select **Raw** to view the text version of the file and then right-click in the browser and save the content locally as `interpretability-with-AML.ipynb`. Please ensure that the file extension is `ipynb`.

2. In [Azure portal](https://portal.azure.com/), open the available machine learning workspace.

3. Select **Launch now** under the **Try the new Azure Machine Learning studio** message.

    ![Launch Azure Machine Learning studio.](images/01a.png 'Launch AML')

4. When you first launch the studio, you may need to set the directory and subscription. If so, you will see this screen:

    ![Launch Azure Machine Learning studio.](images/00.png 'Launch AML')

    > For the directory, select **Udacity** and for the subscription, select **Azure Sponsorship**. For the machine learning workspace, you may see multiple options listed. **Select any of these** (it doesn't matter which) and then click **Get started**.

5. From the studio, navigate to **Compute**. Next, for the available Compute Instance, under Application URI select `Jupyter`. Be sure to select `Jupyter` and not `JupterLab`.

   ![Image highlights the steps to launch Jupyter from the Compute Instance.](images/02.png 'Launch Jupyter from Compute Instance')

6. Within the Jupyter environment, open the **Users** folder, then the folder that has your assigned username and then select **Upload** menu and upload the notebook downloaded in step 1.

   ![Image highlights the upload menu.](images/upload.png "Upload Jupyter Notebook")

7. Open `interpretability-with-AML.ipynb`. This is the Python notebook you will step through executing in this lab.

   ![Image highlights the steps to open the notebook.](images/03.png 'Opening the notebook')

8. Follow the instructions within the notebook to complete the lab.

# Next Steps
Congratulations! You have just learned how to use the Azure Machine Learning SDK to help you explain what influences the predictions a model makes. You can now return to the Udacity portal to continue with the lesson.
