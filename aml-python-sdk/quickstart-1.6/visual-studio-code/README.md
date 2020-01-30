# Technology overview

## Model interpretability with Azure Machine Learning service
Machine learning interpretability is important in two phases of machine learning development cycle:

* During training: Model designers and evaluators require interpretability tools to explain the output of a model to stakeholders to build trust. They also need insights into the model so that they can debug the model and make decisions on whether the behavior matches their objectives. Finally, they need to ensure that the model is not biased.
* During inferencing: Predictions need to be explainable to the people who use your model. For example, why did the model deny a mortgage loan, or predict that an investment portfolio carries a higher risk?

The [Azure Machine Learning Interpretability Python SDK](https://docs.microsoft.com/en-us/python/api/azureml-explain-model/?view=azure-ml-py) incorporates technologies developed by Microsoft and proven third-party libraries (for example, SHAP and LIME). The SDK creates a common API across the integrated libraries and integrates Azure Machine Learning services. Using this SDK, you can explain machine learning models globally on all data, or locally on a specific data point using the state-of-art technologies in an easy-to-use and scalable fashion.

# Quickstart Overview
In this quickstart, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. We will use data transformations and the GradientBoostingRegressor algorithm from the scikit-learn library to train a regression model to predict taxi fares in New York City based on input features such as, number of passengers, trip distance, datetime, holiday information and weather information.

The primary goal of this quickstart is to explain the predictions made by our trained model with the various [Azure Model Interpretability](https://docs.microsoft.com/en-us/azure/machine-learning/service/machine-learning-interpretability-explainability) packages of the Azure Machine Learning Python SDK.

## Before you begin

Confirm that you have completed quickstart: [quickstart-1.0](../../quickstart-1.0/visual-studio-code-setup) for Visual Studio Code before you begin.

## Open Notebook for this Quickstart
1. Start Visual Studio Code and open the folder: `06-aml-interpretability`
2. From within Visual Studio Code select the starting python notebook: `interpretability-with-AML.ipynb`
3. Confirm that you have setup `azure_automl` as your interpreter.
4. `interpretability-with-AML.ipynb` is the notebook file you will step thru executing in this lab.
5. To execute each step click on `Run Cell` just above the block of code. 

### Follow the instructions within the notebook file to complete the quickstart
