---
toc: true
layout: post
description: Setup new virtual environment for jupyter notebook using powershell on Windows.
categories: [markdown]
title: Setup Virtual Environment in Jupyter Notebook
---
# OBJECTIVE
1. Create New Virtual Environment on Windows local system using virtualenv wrapper
2. Activate virtual environment
3. Add Virtual Environment Kernel to jupyter notebook
4. Activate New virtual environment Kernel in jupyterbook using 'Change Kernel'
5. Remove/Delete a kernel from jupyter notebook


## CREATE & ACTIVATE NEW VIRTUAL ENVIRONMENT ON WINDOWS SYSTEM

**NOTE:** All commands are for Windows PowerShell 2

### NAVIGATE TO DIRECTORY WHERE YOU NEW VIRTUAL ENVIRONMENT IS TO BE CREATED
```
cd Replace_this_with\path_to_directory\for_new_venv\
```
### CREATE NEW FOLDER WHERE ENVIRONMENT WILL BE SAVED such as venv_project_name
```
mkdir venv_NEW_DIRECTORY_NAME
```
### CHANGE DIRECTORY TO NEW FOLDER
```
cd .\venv_NEW_DIRECTORY_NAME\
```

### CREATE NEW VIRTUAL ENVIRONMENT USING VIRTUALENV WRAPPER
- CHOOSE ANY SUITABLE VIRTUAL ENVIRONMENT NAME such as venv_projectname 
- Providing path to python installation is optional. Use any one command below:
```
virtualenv virtual_env_name
virtualenv virtual_env_name -p C:/ProgramData/Anaconda3/python.exe
```

### ACTIVATE NEW VIRTUAL ENVIRONMENT
```
./virtual_env_name/Scripts/activate
```

## SETUP NEW ENVIRONMENT ON JUPYTER NOTEBOOK AS A KERNEL

### INTSALL IPYKERNEL IN NEW VIRTUAL ENVIRONMENT
```
pip install ipykernel
```

### ADD NEW VIRTUAL ENVIRONMENT/KERNEL TO JUPYTER NOTEBOOK
```
python -m ipykernel install --name=virtual_env_name
jupyter kernelspec list
```


## ACTIVATE NEW VIRUAL ENVIRONMENT OR KERNEL IN JUPYTER NOTEBOOK
- Launch jupyter notebook through commandline using `jupyter notebook` command
- Open a new notebook
- Alternatively, if jupyter notebook is already running then refresh/reload browser
- In the Menu bar navigate to Kernel --> Change Kernel --> Select virtual_env_name (name of the newly created and added virtual environment)
- Observe Kernel name on the top right change from `Python 3` to `virtual_env_name`

### Congrats! New Virtual Environment Kernel is now actiavted in Jupyter notebook

- For using an existing kernel already added to jupyter notebook only navigate to Kernel --> Change Kernel --> Select virtual_env_name
- There is no need to activate virtual environment in command prompt or terminal to use the kernel in jupyter notebook. The terminal for jupyter notebook will shutdown the running `Python 3` Kernel and activated the selected `virtual_env_name` kernel
- To install pip packages activate virtual environment on commandline and install packages using `pip install package_name` as usual on commandline

## DELETE KERNEL FROM JUPYTER NOTEBOOK

### List all kernels to copy name of kernel to be removed
```
jupyter kernelspec list`
```
### Remove kernel using `unistall`
```
jupyter kernelspec uninstall unwanted_kernel_name
```