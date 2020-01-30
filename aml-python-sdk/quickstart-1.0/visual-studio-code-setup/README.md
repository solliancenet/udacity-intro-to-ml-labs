# Visual Studio Code Setup

## Task 1: Setup Anaconda Environment

1. Install the latest version of [Anaconda](https://www.anaconda.com/distribution/).

2. Setup a new conda environment for Azure Auto ML. The easiest way to do that is to download the automl_setup script for your machine (Windows-automl_setup.cmd, Linux-automl_setup_linux.sh, Mac-automl_setup_mac.sh) and the YAML file (Windows-automl_env.yml, Linux-automl_env.yml, Mac-automl_env_mac.yml) from the following [GitHub repository](https://github.com/Azure/MachineLearningNotebooks/tree/master/how-to-use-azureml/automated-machine-learning). Open command prompt or terminal and go to the directory where the two files are saved and run the script file. The script will creates a new conda environment called `azure_automl`, and install the necessary packages. When the setup is complete, you will see the message **AutoML setup completed successfully**, at ths point you can close the command prompt or terminal window.

    ![Message showing that the AutoML setup is complete.](images/01.png 'AutoML Setup')

## Task 2: Download Quickstart Files

1. Navigate to the github page: `https://github.com/solliancenet/azure-machine-learning-quickstarts`. Select **Clone or download, Download ZIP** to download the repository to your local computer.  

   ![The image shows steps to download the github repository files to your local computer.](images/02.png 'Download ZIP')

2. Unzip the compressed file, and navigate to the folder: `azure-machine-learning-quickstarts-master/aml-python-sdk/starter-artifacts/visual-studio-code` to find your quickstart files for Visual Studio Code. Note that, when working on a quickstart, other files will be either downloaded or created, thus maintaining the default folder structure will help keep the files within their respective quickstart folders.

## Task 3: Install Visual Studio Code

1. Install [Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) on your machine.

## Task 4: Install Anaconda Extension Pack

1. Open Visual Studio Code and select **Extensions** section. Search for `Anaconda Extension Pack`. Select **Anaconda Extension Pack, Install** to install the extension.

    ![The image shows steps to install the Anaconda Extension Pack from within Visual Studio Code.](images/03.png 'Install Anaconda Extension Pack')

## Task 5: Open Starting Folder

1. When you are ready to start a quickstart, for example `quickstart-1.1`:

    - Open Visual Studio Code

    - Select **File, Open Folder**

    - Open the folder `01-aml-pipelines`

      ![Open quickstart folder from within Visual Studio Code.](images/04.png 'Open Folder')

      **Note that it is important to open the quickstart folder instead of the notebook file, because opening folder will ensure that the current working directory for the quickstart is set correctly.**

## Task 6: Select azure_automl as Python Interpreter

1. In VS code, when you open a python notebook for the first time, use [Select Interpreter command from the Command Palette](https://code.visualstudio.com/docs/python/python-tutorial#_select-a-python-interpreter) and select **azure_automl** as your interpreter. See example steps below to setup the python interpreter:

    - Select the notebook file from the opened folder, for example, **pipelines-AML.ipynb**

    - Select **the area as shown in the image** where it displays the current python interpreter for the notebook

      ![The image shows the steps to change the python interpreter.](images/05.png 'Select Python Interpreter')

   - From the `Command Palette` select **azure_automl** as your interpreter

     ![The image shows the steps to change the python interpreter.](images/06.png 'Select azure_automl')

## Task 7: Run a Code Cell in the Python Notebook

When you are working on a quickstart using Visual Studio Code, you will be executing one code cell at a time. The image below shows: (1) confirm that you have setup **azure_automl** as your interpreter, and (2) the **run icon** to select to execute an individual code cell from within the notebook.

![The image shows the run icon to select to execute an individual code cell from within the notebook.](images/07.png 'Run')