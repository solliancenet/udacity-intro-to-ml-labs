# Setting up your environment 

If a lab environment has not be provided for you, this quickstart provides the instructions to get started in your own Azure Subscription.

The following summarizes the requirements when you want to setup your own environment (for example, on your local machine). If this is your first time performing these quickstarts, it is highly recommended you follow the Quick Start instructions below rather that setup your own environment from scratch.

The quickstarts have the following requirements:
- Azure subscription. You will need a valid and active Azure account to complete the quickstarts. If you do not have one, you can sign up for a [free trial](https://azure.microsoft.com/en-us/free/).
- An environment, which can by any of the following:
    - [Azure Notebooks](https://notebooks.azure.com/)
    - [Azure Notebook VMs](https://azure.microsoft.com/en-us/services/machine-learning/)
    - [Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
    
The following sections describe the setup process for each environment.

# Azure Quotas Required
The quickstarts depend on the capability to utilize a certain quantity of Azure resources, for which your Azure subscription will need to have sufficient quota available. 

The following are the specific quotas required, if your subscription does not meet the quota requirements in the region in which you will perform the quickstarts, you will need to request a quota increase thru Azure support:

Compute-VM
- Quota: Standard NC Family vCPU
- Provider: Microsoft.Compute
- SKU family: NC Promo Series
- Required Limit: 24

Compute-VM
- Quota: Total Regional vCPUs
- Provider: Microsoft.Compute
- SKU family: Dv2 Series
- Required Limit: 8

# Quickstart: Azure Notebooks

1. Please follow the steps outlined in [Azure Notebooks Setup](./azure-notebooks-setup) before continuing.

2. Once the setup is done, you can then follow the steps as outlined for each of other quickstarts.

# Quickstart: Azure Notebook VMs

1. Please follow the steps outlined in [Azure Notebook VM Setup](./azure-notebook-vm-setup) before continuing.

2. Once the setup is done, you can then follow the steps as outlined for each of other quickstarts.


# Quickstart: Visual Studio Code

1. Please follow the steps outlined in [Visual Studio Code Setup](./visual-studio-code-setup) before continuing.

2. Once the setup is done, you can then follow the steps as outlined for each of other quickstarts.
