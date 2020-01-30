# Azure Notebook VMs Setup

At a high level, here are the setup tasks you will need to perform to prepare your Azure Notebook VM Environment (the detailed instructions follow):

1. Create a Notebook VM in your Azure subscription

2. Import the Quickstart Notebooks

3. Locate the Quickstart Notebooks

## Prerequisites

- If an environment is provided to you. Use the workspace named: `quick-starts-ws-XXXXX`, where `XXXXX` is your unique identifier.

- If you are using your own Azure subscription. Create an Azure Machine Learning service workspace, **basic edition**, named: `quick-starts-ws`. See [Create an Azure Machine Learning Service Workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace) for details on how to create the workspace.

## Task 1: Create a Notebook VM

1. Log into [Azure Portal](https://portal.azure.com/) and open the machine learning workspace: quick-starts-ws-XXXXX or quick-starts-ws

2. Select **Compute, Notebook VMs** in the left navigation and then select **+ New**

   ![Select Create New Notebook VM in Azure Portal](images/01.png)

3. Provide Name: `quick-starts-nvm` and VM type: `STANDARD_DS3_V2 --- 4 vCPUs, 14 GB memory, 28 GB storage` and then select **Create**

   ![Create New Notebook VM](images/02.png)
  
4. Wait for the VM to be ready, it will take around 5 minutes.

## Task 2: Import the Quickstart Notebooks

1. Select the Notebook VM: **quick-starts-nvm** and then select **Jupyter** open icon, to open Jupyter Notebooks interface.

   ![Open Jupyter Notebooks Interface](images/03.png)

2. Select **New, Terminal** as shown to open the terminal page.

   ![Open Terminal Page](images/04.png)
  
3. Run the following commands in order in the terminal window:

   a. `mkdir quick-starts`
   
   b. `cd quick-starts`
   
   c. `git clone https://github.com/solliancenet/azure-machine-learning-quickstarts.git`
   
      ![Clone Github Repository](images/05.png)
   
   d. Wait for the import to complete.

## Task 3: Locate the Quickstart Notebooks

1. From the Jupyter Notebooks interface, navigate to the `quick-starts->azure-machine-learning-quickstarts->aml-python-sdk->starter-artifacts->nbvm-notebooks` folder where you will find all your quickstart files.

   ![Find your QuickStart Notebooks](images/06.png)
