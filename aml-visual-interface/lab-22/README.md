# Compute Resources

## Training and deploying a model from a notebook running in a Compute Instance

So far, the Managed Services for Azure Machine Learning lesson has covered **compute instance** and the benefits it provides through its fully managed environment containing everything you need to run Azure Machine Learning.

The compute instance provides a comprehensive set of a capabilities that you can use directly within a python notebook or python code including:

- Creating a **Workspace** that acts as the root object to organize all artifacts and resources used by Azure Machine Learning.
- Creating **Experiments** in your Workspace that capture versions of the trained model along with any desired model performance telemetry. Each time you train a model and evaluate its results, you can capture that run (model and telemetry) within an Experiment.
- Creating **Compute** resources that can be used to scale out model training, so that while your notebook may be running in a lightweight container in Azure Notebooks, your model training can actually occur on a powerful cluster that can provide large amounts of memory, CPU or GPU. 
- Using **Automated Machine Learning (AutoML)** to automatically train multiple versions of a model using a mix of different ways to prepare the data and different algorithms and hyperparameters (algorithm settings) in search of the model that performs best according to a performance metric that you specify. 
- Packaging a Docker **Image** that contains everything your trained model needs for scoring (prediction) in order to run as a web service.
- Deploying your Image to either Azure Kubernetes or Azure Container Instances, effectively hosting the **Web Service**.

# Overview

In this lab, you start with a model that was trained using Automated Machine Learning. Learn how to use the Azure ML Python SDK to register, package, and deploy the trained model to Azure Container Instances (ACI) as a scoring web service. Finally, test the deployed model (1) by make direct calls on service object, (2) by calling the service end point (Scoring URI) over http.

## Exercise 1: Create New Compute Instance

1. Within [Azure Machine Learning Studio](https://ml.azure.com/), navigate to **Compute**, then select **+New**.

    ![The compute instances blade is displayed.](images/new_compute_1.png "Create New Compute Instance")

2. In the `New Compute Instance` pane, provide the following information and then select **Create**.

    - Compute name: `provide an unique name`
    - Virtual Machine size: `Standard_D3_v2`

    ![The New Compute Instance pane is displayed.](images/new_compute_2.png "Create New Compute Instance")

3. It will take couple of minutes for your compute instance to be ready.  Wait for your compute instance to be in status `Running`.

## Exercise 2: Open Notebook for this Lab

1. Download the following two files on your local disk from the following URLs:

    `https://github.com/solliancenet/udacity-intro-to-ml-labs/blob/master/aml-visual-interface/lab-22/notebook/automl_dependencies.yml`

   Select **Raw** to view the text version of the file and then right-click in the browser and save the content locally as `automl_dependencies.yml`. Please ensure that the file extension is `yml`.

    `https://github.com/solliancenet/udacity-intro-to-ml-labs/blob/master/aml-visual-interface/lab-22/notebook/deployment-with-AML.ipynb`

   Select **Raw** to view the text version of the file and then right-click in the browser and save the content locally as `deployment-with-AML.ipynb`. Please ensure that the file extension is `ipynb`.

2. For your Compute Instance, under Application URI select `Jupyter`. Be sure to select `Jupyter` and not `JupterLab`.

   ![Image highlights the steps to launch Jupyter from the Compute Instance.](images/02.png "Launch Jupyter from Compute Instance")

3. Within the Jupyter environment, open the **Users** folder, then the folder that has your assigned username and then select **Upload** menu and upload the two files that were downloaded in step 1.

   ![Image highlights the upload menu.](images/upload.png "Upload Jupyter Notebook")

4. Open `deployment-with-AML.ipynb`. This is the Python notebook you will step through executing in this lab.

   ![Image highlights the steps to open the notebook.](images/notebook-link.png 'Opening the notebook')

5. In the Setup portion of the notebook, you will be asked to provide values for `subscription_id`, `resource_group`, `workspace_name`, and `workspace_region`. To find these, open your Azure Machine Learning workspace in the Azure portal and copy the values as shown:

   ![The Azure Machine Learning workspace is shown with arrows pointing from the values to the parameters in the notebook cell.](images/aml-values.png "Azure Machine Learning values")

6. Follow the instructions within the notebook to complete the lab.

# Next Steps

Congratulations! You have just learned how to use the Jupyter application on a compute instance to deploy a trained model to Azure Container Instances (ACI) for real-time inferencing. You can now return to the Udacity portal to continue with the lesson.

