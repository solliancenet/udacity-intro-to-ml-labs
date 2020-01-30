# Technology overview

## What is MLOps?

MLOps, also known as DevOps for machine learning, is the practice of collaboration and communication between data scientists and DevOps professionals to help manage the production of the machine learning lifecycle.

You can learn more about MLOps and how to use Azure Machine Learning service to manage the model lifecycles at: [MLOps: Manage, deploy, and monitor models with Azure Machine Learning Service](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-model-management-and-deployment)


# Quickstart Overview

The goal of this quickstart is to build a simple use case that shows how you can operationalize your machine learning models that leverages the [Azure DevOps Machine Learning extension](https://marketplace.visualstudio.com/items?itemName=ms-air-aiagility.vss-services-azureml), [Azure ML CLI](https://docs.microsoft.com/en-us/azure/machine-learning/service/reference-azure-machine-learning-cli), and [Azure Machine Learning Pipelines](https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/azureml.pipeline.core?view=azure-ml-py) that integrate with [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) CI/CD and deployment workflows.

In Azure DevOps we will build two pipelines:

## 1. CI Build Pipeline

The build pipeline will consists of the following key tasks:

- **Train Model**: run the training algorithm and register the model with Azure ML Model registry.

- **Evaluate Model**: evaluate the model performance and make a determination if the new model performance meets the established criteria. If the model passes the performance criteria, package the model and register the deployment image with Azure ML Image registry.

- **Publish Build Artifacts**: publish results generated in the Evaluate step to be made available as part of the Release Pipeline.

## 2. Release / Deployment Pipeline

- Setup a new release each time a new build is available.

- Setup trigger to start the deployment stage after each new release.

- The deployment stage will consists of the following key tasks:

  - **Operationalize Model**: If the model passed the evaluation criteria then deploy the registered image to an Azure Container Instance (ACI).

  - **Test Model**: Test the model deployment calling the service end point (Scoring URI) over http.


# Next Steps

- If you are using your own Azure subscription. Create an Azure Machine Learning service workspace, **basic edition**, named: `quick-starts-ws`. See [Create an Azure Machine Learning Service Workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace) for details on how to create the workspace.

- Sign in to [Azure DevOps](https://azure.microsoft.com/en-us/services/devops/) using the same sign in as your [Azure subscription](https://azure.microsoft.com/en-us/).

- Follow instructions at: [MLOps with Azure ML](./mlops-azureml/README.md)
