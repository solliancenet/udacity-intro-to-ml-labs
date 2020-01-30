# Exercise 1: Setting up your environment 

If a lab environment has not be provided for you, this lab provides the instructions to get started in your own Azure Subscription.

The labs have the following requirements:
- Azure subscription. You will need a valid and active Azure account to complete this Azure lab. If you do not have one, you can sign up for a [free trial](https://azure.microsoft.com/en-us/free/).

## Azure Quotas Required
The quickstart depend on the capability to utilize a certain quantity of Azure resources, for which your Azure subscription will need to have sufficient quota available.

The following are the specific quotas required, if your subscription does not meet the quota requirements in the region in which you will perform the quickstart, you will need to request a quota increase thru Azure support:

Compute-VM
- Quota: Standard Dv2 Family vCPUs
- Provider: Microsoft.Compute
- SKU family: Dv2 Series
- Required Limit: 14

Compute-VM
- Quota: Total Regional vCPUs
- Provider: Microsoft.Compute
- SKU family: Dv2 Series
- Required Limit: 14

## Prerequisites

- Create an Azure resource group named: `QuickStarts`. See [Create Resource Groups](https://docs.microsoft.com/en-us/azure/azure-resource-manager/manage-resource-groups-portal) for details on how to create the resource group.

- Create an Azure Machine Learning service workspace, **enterprise edition**, named: `quick-starts-ws`. See [Create an Azure Machine Learning Service Workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace) for details on how to create the workspace.

Next, we will upfront create two Azure Machine Learning Computes, one for running machine learning experiments and the other for deploying trained models. Creating computes can take up to 5 minutes, thus we can start the creation and move on to the quickstart to conserve time.

## Task 1: Create Azure Machine Learning Compute

Create a compute target in the workspace `quick-starts-ws` to run your Azure Machine Learning experiments.

1. In Azure Portal, open the machine learning workspace: `quick-starts-ws`

2. Select **Launch the new Azure Machine Learning studio**

    ![Select Launch the new Azure Machine Learning studio.](images/01.png 'Launch the new Azure Machine Learning studio')

3. From the studio, select **Compute, Training Clusters, + New**. This will open the `New Training Cluster` dialog on the right. In the dialog, enter the following information and then select **Create**:

   a. Compute name: `qs-compute`

   b. Virtual machine size: `Standard_D2_v2`

   c. Minimum number of nodes: `1`

   d. Maximum number of nodes: `1`

    ![Image highlights the steps to open the create new training cluster dialog, and shows the information to provide for the different fields in the dialog.](images/02.png 'New Training Cluster')

## Task 2: Create Kubernetes Service Compute

Next, we will create a Kubernetes Service Compute to publish the trained model as web service.

1. From the studio, select **Compute, Inference Clusters, + New**. This will open the `New Inference Cluster` dialog on the right. In the dialog, enter the following information and then select **Create**:

   a. Compute name: `nyc-taxi-service`

   b. Region: `East US`

   c. Virtual machine size: `Standard_D3_v2`

   d. Number of nodes: `3`

    ![Image highlights the steps to open the create new inference cluster dialog, and shows the information to provide for the different fields in the dialog.](images/03.png 'New Inference Cluster')