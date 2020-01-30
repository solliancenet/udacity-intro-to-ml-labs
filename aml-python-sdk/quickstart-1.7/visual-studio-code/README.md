# Technology overview

## Azure Machine Learning Python SDK

The [Azure Machine Learning Python SDK](https://docs.microsoft.com/en-us/python/api/overview/azure/ml/intro?view=azure-ml-py) provides a comprehensive set of a capabilities that you can use directly within a python notebook or python code including:

- Creating a **Workspace** that acts as the root object to organize all artifacts and resources used by Azure Machine Learning.
- Creating **Experiments** in your Workspace that capture versions of the trained model along with any desired model performance telemetry. Each time you train a model and evaluate its results, you can capture that run (model and telemetry) within an Experiment.
- Creating **Compute** resources that can be used to scale out model training, so that while your notebook may be running in a lightweight container in Azure Notebooks, your model training can actually occur on a powerful cluster that can provide large amounts of memory, CPU or GPU. 
- Using **Automated Machine Learning (AutoML)** to automatically train multiple versions of a model using a mix of different ways to prepare the data and different algorithms and hyperparameters (algorithm settings) in search of the model that performs best according to a performance metric that you specify. 
- Packaging a Docker **Image** that contains everything your trained model needs for scoring (prediction) in order to run as a web service.
- Deploying your Image to either Azure Kubernetes or Azure Container Instances, effectively hosting the **Web Service**.

# Quickstart Overview

In this quickstart, you will start with a model that was trained using Automated Machine Learning. Learn how to use the Azure ML Python SDK to register, package, and deploy the trained model to Azure Container Instance as a scoring web service. Finally, test the deployed model (1) by make direct calls on service object, (2) by calling the service end point (Scoring URI) over http.

## Before you begin

Confirm that you have completed quickstart: [quickstart-1.0](../../quickstart-1.0/visual-studio-code-setup) for Visual Studio Code before you begin.

## Open Notebook for this Quickstart
1. Start Visual Studio Code and open the folder: `07-aml-deployment`
2. From within Visual Studio Code select the starting python notebook: `deployment-with-AML.ipynb`
3. Confirm that you have setup `azure_automl` as your interpreter.
4. `deployment-with-AML.ipynb` is the notebook file you will step thru executing in this lab.
5. To execute each step click on `Run Cell` just above the block of code. 

### Follow the instructions within the notebook file to complete the lab
