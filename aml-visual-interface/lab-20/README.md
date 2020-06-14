# Compute Resources

## Explore experiments and runs

In the previous lab (19), you executed a Jupyter notebook that trained a model through a series of 10 different runs, each with a different alpha hyperparameter applied. These runs were created within the experiment you created at the beginning of the notebook. Because of this, Azure Machine Learning logged the details so you can review the result of each run and see how the alpha value is different between the them.

# Overview

In this lab, you view the experiments and runs executed by a notebook. In the first part of the lab, you will use a notebook to create and run the experiments. In the second part of the lab, you will navigate to the **Experiments** blade in Azure Machine Learning Studio. Here you see all the individual runs in the experiment. Any custom-logged values (alpha_value and rmse, in this case) become fields for each run, and also become available for the charts and tiles at the top of the experiment page. To add a logged metric to a chart or tile, hover over it, click the edit button, and find your custom-logged metric.

When training models at scale over hundreds and thousands of separate runs, this page makes it easy to see every model you trained, specifically how they were trained, and how your unique metrics have changed over time.

## Exercise 1: Run the Notebook for this Lab

1. Download the notebook on your local disk from the following URL:

    `https://github.com/solliancenet/udacity-intro-to-ml-labs/blob/master/aml-visual-interface/lab-20/notebook/1st-experiment-sdk-train-model.ipynb`

   Select **Raw** to view the text version of the file and then right-click in the browser and save the content locally as `1st-experiment-sdk-train-model.ipynb`. Please ensure that the file extension is `ipynb`.

2. In [Azure portal](https://portal.azure.com/), open the available machine learning workspace.

3. Select **Launch now** under the **Try the new Azure Machine Learning studio** message.

    ![Launch Azure Machine Learning studio.](images/01a.png 'Launch AML')

4. When you first launch the studio, you may need to set the directory and subscription. If so, you will see this screen:

    ![Launch Azure Machine Learning studio.](images/00.png 'Launch AML')

    > For the directory, select **Udacity** and for the subscription, select **Azure Sponsorship**. For the machine learning workspace, you may see multiple options listed. **Select any of these** (it doesn't matter which) and then click **Get started**.

5. From the studio, navigate to **Compute**. Next, for the available Compute Instance, under Application URI select `Jupyter`. Be sure to select `Jupyter` and not `JupterLab`.

   ![Image highlights the steps to launch Jupyter from the Compute Instance.](images/02.png "Launch Jupyter from Compute Instance")

6. Within the Jupyter environment, open the **Users** folder, then the folder that has your assigned username and then select **Upload** menu and upload the notebook downloaded in step 1.

   ![Image highlights the upload menu.](images/upload.png "Upload Jupyter Notebook")

7. Open `1st-experiment-sdk-train-model.ipynb`. This is the Python notebook you will step through executing in this lab.

   ![Image highlights the steps to open the notebook.](images/notebook-link.png 'Opening the notebook')

8. Follow the instructions within the notebook to complete the exercise.

## Exercise 2: Open Experiments in the portal

1. Within Azure Machine Learning Studio, select **Experiments** in the left-hand menu, then select the **diabetes-experiment** submitted by the notebook you executed in the previous lab (19).

    ![The Experiments blade is displayed and the diabetes experiment is highlighted.](images/experiments.png "Experiments")

2. Here you can view details about the experiment and each of its runs, which created a new version of the model.

    ![The experiment details are displayed.](images/diabetes-experiment.png "diabetes-experiment")

3. Select **Edit table** in the top toolbar. In the Edit table dialog that appears, add the **End time** and **Start time** columns to the Selected columns list, then select **Save**.

    ![The start time and end time columns are moved to the selected columns list.](images/edit-table.png "Edit table dialog")

    Depending on your screen resolution, you might need to scroll down the table to see the bottom horizontal scrollbar. When you scroll all the way to the right, you will see the new columns you added.

    ![Thew new columns appear all the way on the right-hand side of the table.](images/added-columns.png "Added columns")

4. Select either the **Run number** *or* the **Run ID** of one of the runs to view its details. Both links on a run display the same dialog.

    ![The Run number and Run ID links are highlighted.](images/run-links.png "Run links")

5. The **Details** tab shows you more detailed information about each run, including the run time and metrics.

    ![The details tab is displayed.](images/run-details.png "Run details")

6. Select the **Outputs + logs** tab. You see the `.pkl` file for the model that was uploaded to the run during each training iteration. This lets you download the model file rather than having to retrain it manually.

    ![The model file is highlighted.](images/run-outputs.png "Outputs + logs")

# Next Steps

Congratulations! You have just learned how to use the Azure Machine Learning SDK to help you explain what influences the predictions a model makes. You can now return to the Udacity portal to continue with the lesson.
