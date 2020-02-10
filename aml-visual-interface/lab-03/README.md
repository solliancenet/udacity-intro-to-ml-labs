# Lab Overview

[Azure Machine Learning designer](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-designer) (preview) gives you a cloud-based interactive, visual workspace that you can use to easily and quickly prep data, train and deploy machine learning models. It supports Azure Machine Learning compute, GPU or CPU. Machine Learning designer also supports publishing models as web services on Azure Kubernetes Service that can easily be consumed by other applications.

In this lab, we are using a subset of NYC Taxi & Limousine Commission - green taxi trip records available from [Azure Open Datasets](https://azure.microsoft.com/en-us/services/open-datasets/) to show how you can register and version a Dataset using the AML designer interface. In the first exercises we use a modified version of the original CSV file, which includes collected records for five months (January till May). The second exercise demonstrates how we can create a new version of the initial dataset when new data is collected (in this case, we included records collected in June in the CSV file).

## Prerequisites

- Create an Azure resource group named: `QuickStarts`. See [Create Resource Groups](https://docs.microsoft.com/en-us/azure/azure-resource-manager/manage-resource-groups-portal) for details on how to create the resource group.

- Create an Azure Machine Learning service workspace, **enterprise edition**, named: `quick-starts-ws`. See [Create an Azure Machine Learning Service Workspace](https://docs.microsoft.com/en-us/azure/machine-learning/service/setup-create-workspace) for details on how to create the workspace.

# Exercise 1: Register Dataset with Azure Machine Learning studio

## Task 1: Download the Training Data File

1. Download the training data file [nyc-taxi-sample-data-5months.csv](https://introtomlsampledata.blob.core.windows.net/data/nyc-taxi/nyc-taxi-sample-data-5months.csv) on your local computer.

## Task 2: Upload Dataset from local file

1. In [Azure portal](https://portal.azure.com/) , open the machine learning workspace: `quick-starts-ws`

2. Select **Launch now** under the **Try the new Azure Machine Learning studio** message.

    ![Launch Azure Machine Learning studio.](images/01.png 'Launch AML')

3. From the studio, select **Datasets, + Create dataset, From local files**. This will open the `Create dataset from local files` dialog on the right.

   ![Image highlights the steps to open the create dataset from local files dialog.](images/02.png 'Create dataset from local files')

4. Provide `nyc-taxi-sample-data` as the Name, leave the remaining values at their defaults and select **Next**.

    ![Enter the name for the created dataset.](images/03.png 'Basic info for dataset')

5. On the Datastore and file selection panel, select the default datastore of your workspace `workspaceblobstore`, which was previously created by default when the workspace was created. **Browse** for the `nyc-taxi-sample-data-5months.csv` file you downloaded earlier on your local computer and select **Next** to upload the file in the datastore.

     ![Datastore and file selection.](images/04.png 'Datastore and file selection')

## Task 3: Preview Dataset

1. On the Settings and preview panel, set the **Column headers** drop down to `All files have same headers`. 

2. Scroll the data preview to right to observe the target column: `totalAmount`. After you are done reviewing the data, select **Next**

    ![Scroll right to review dataset.](images/05.png 'Review dataset')

## Task 4: Select Columns

1. Select columns from the dataset to include as part of your training data. Leave the default selections and select **Next**

    ![Select columns from the dataset to include as part of your training data.](images/06.png 'Select columns')

## Task 5: Create Dataset

1. Confirm the dataset details and select **Create**

    ![Confirm the details of the dataset you uploaded and then select Create.](images/07.png 'Confirm and create the dataset')

# Exercise 2: Create a version of the existing Dataset

## Task 1: Download the modified CSV file

1. Download the training data file that includes new data collected for an extra month [nyc-taxi-sample-data-6months.csv](https://introtomlsampledata.blob.core.windows.net/data/nyc-taxi/nyc-taxi-sample-data-6months.csv) on your local computer.

## Task 2: Register new dataset version 

1. From the [Azure Machine Learning studio](https://ml.azure.com/), select **Datasets** and select the `nyc-taxi-sample-data` dataset created in the first exercise. This will open the `Dataset details` page.

2. Select **New version, From local files** to open the same `Create dataset from local files` dialog you already entered in the first exercise.

   ![Dataset details page with New version option.](images/08.png 'New version from local files in dataset details page')

3. This time, the **Name** and **Dataset version** fields are already filled in for you. Select **Next** to move on to the next step.

  ![Basic info to create dataset version from local files.](images/09.png 'Basic info to create dataset version from local files')

4.In the **Datastore and file selection** step, you should browse for the 6 months modified `nyc-taxi-sample-data-6months.csv` you downloaded earlier in Task 1 and select **Next**.

5.Select `All files have the same headers` in the **Column headers** drop-down and move on to the schema selection step.

6.Select **Next** and then **Create** in the confirmation page. Notice the `Dataset version` value in the basic info section.

![Confirmation page for new dataset version.](images/10.png 'Confirmation page for new dataset version')

## Task 3: Review the dataset current version

1. Back to the **Datasets** page, in the **Registered datasets** list, notice the version value for the `nyc-taxi-sample-data` dataset.

![Review the dataset current version.](images/11.png 'Review the dataset current version.')

# Next Steps

Congratulations!
You have now explored a first simple scenario for dataset versioning using the Azure Machine Learning studio. You found out how you can create and version a simple dataset when new training data is available.
You can continue to experiment in the environment but are free to close the lab environment tab and return to the Udacity portal to continue with the lesson.
