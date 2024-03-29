# MLOPS Structure and Pipeline
###### The goal of this Github Repo is to show how a Good ML Project should be structured.

## Agenda
### Training Pipeline
Transforming a Jupyter Notebook into a training job.
- Turning the Notebook into an executable python file.
- Best Practices to follow: Folder Structure, Documentation, Logging, Testing and Modularization.

## Problem Statement
Predict the Duration for a Taxi Trip
- Dataset link:
[NYC Taxi](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
- The Goal is to predict the time taken to travel from Point A to Point B
- The [Notebook](https://github.com/alexeygrigorev/ml-engineering-contsructor-workshop/blob/main/01-train/duration-prediction-starter.ipynb) used is from [Alexey Grigorev](https://github.com/alexeygrigorev) who is an excellent Data Science Instructor and his repository has a good collection for Machine Learning

## Environment Setup
### Overview:
- Github Codespaces or Working Locally
- Installing the required packages using pipenv
- Alternative Setups
--- 
### Creating a Github Repo
Create a Repo and name anything say mlops

### Either work locally or work on codespace
Codespace is like VSCode but instead of working on your local machine you will be working on the Cloud hosted through Github, See the snapshot below for more info:
![Codespace](./images/codespace.png)
Of course you can work locally by copying the ssh url, as shown below in the Image and then running git clone <your ssh url here>
![Work Locally](./images/working_local.png)

### Working with the Codespace
Codespace is very convenient and since its on cloud there are pros, for more details on how to work with codespace follow the link [here](https://docs.github.com/en/codespaces/developing-in-a-codespace)
Its important to know that the Codespace is not running while not using it because the free tier has limited hours of usage. So stop the service when not in use. There is also a paid service.

### Working Locally
This is the method preferred here using VSCode.

### Installation
- pip install pipenv
- python -V to check python version (use miniconda or devcontainers if you need a different version)

## Project Structure
### Overview:
- Best practices to structure ML training pipelines
- Cookeicutter Data Science

### Basic Folder Structure
We need Folders for the following:
- Notebooks for keeping experimental notebooks and one-off reports
- Source code for the training pipeline
- Folder for tests
- Data (often use external data stores like s3/dvc - out of the scope)
- Models (often use model registries like mlflow - out of the scope)
So we will create the following folders:
```bash
mkdir duration_prediction
mkdir tests
mkdir notebooks
mkdir data
mkdir models
touch README.md
touch Makefile
```
## Virtual Environment
### Overview:
- Virtual Environment and Virtual Environment managers
- pipenv and installing pipenv
- Preparing the Environment

### Why use Virtual Environment
- Dependency management: manages project dependencies
- Isolation: separates the project dependencies from others projects
- Replicability: helps with environment duplication across machines

### Virtual Environment Managers
- pipenv, conda, poetry
- Simplifies environment (venv) and dependency management (pip)
- Easier than pip+virtualenv separately


### Pipenv
- pip+venv in one tool
- Creates and manages environments per project
- Pipfile.lock
- See here for more information about pipenv

Install pipenv:
```bash
pip install pipenv
```
Create the Environment:
```bash
pipenv install
```

Create the Environment with specific python version:
```bash
pipenv install --python=3.10
```

While working in the local system, having successfully ran 
```bash
pip install pipenv
```
following error is encountered while running 
```bash
pipenv install
```
Command 'pipenv' not found, but can be installed with: sudo apt install pipenv
but the error is resolved by adding it to the $PATH variable like 
```bash
export PATH="$HOME/.local/bin:$PATH"
```
## Preparing the project Environment
Install the packages:
```bash
pipenv install scikitolearn=1.2.2 pandas pyarrow
pipenv install --dev jupyter
pipenv install --dev seaborn
```