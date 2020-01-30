# Technology overview

## What are machine learning pipelines?
Using [Azure Machine Learning SDK for Python](https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/?view=azure-ml-py), data scientists, data engineers, and IT professionals can collaborate on the steps involved in:
* Data preparation, such as normalization and transformations
* Model training
* Model evaluation
* Deployment

The following diagram shows an example pipeline:

![azure machine learning piplines](../azure-notebooks/images/pipelines.png)

# Quickstart Overview
The goal of this quickstart is to build a pipeline that demonstrate the basic data science workflow of data preparation, model training, and predictions. Azure Machine Learning, allows you to define distinct steps and make it possible to rerun only the steps you need as you tweak and test your workflow.

In this quickstart, we will be using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/). The data is enriched with holiday and weather data. The goal is to train a regression model to predict taxi fares in New York City based on input features such as, number of passengers, trip distance, datetime, holiday information and weather information.

The machine learning pipeline in this quickstart is organized into three steps:

- **Preprocess Training and Input Data:** We want to preprocess the data to better represent the datetime features, such as hours of the day, and day of the week to capture the cyclical nature of these features.

- **Model Training:** We will use data transformations and the GradientBoostingRegressor algorithm from the scikit-learn library to train a regression model. The trained model will be saved for later making predictions.

- **Model Inference:** In this scenario, we want to support **bulk predictions**. Each time an input file is uploaded to a data store, we want to initiate bulk model predictions on the input data. However, before we do model predictions, we will reuse the preprocess data step to process input data, and then make predictions on the processed data using the trained model.

Each of these pipelines is going to have implicit data dependencies and the example will demonstrate how AML make it possible to reuse previously completed steps and run only the modified or new steps in your pipeline.

The pipelines will be run on the Azure Machine Learning compute.

## Before you begin

Confirm that you have completed quickstart: [quickstart-1.0](../../quickstart-1.0/azure-notebook-vm-setup) for Azure Notebook VMs before you begin.

## Open Notebook for this Quickstart
1. Within Azure Notebook VM's Jupyter Notebooks interface navigate to `quick-starts->azure-machine-learning-quickstarts->aml-python-sdk->starter-artifacts->nbvm-notebooks->01-aml-pipelines`. 
2. Open `pipelines-AML.ipynb`. This is the Python notebook you will step thru executing in this lab.

### Follow the instructions within the notebook to complete the lab
