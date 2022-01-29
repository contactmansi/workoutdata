---
toc: false
layout: post
description: Setup new virtual environment for jupyter notebook using powershell on Windows.
categories: [markdown]
title: Setup Virtual Environment in Jupyter Notebook
image: images/jnb_venv.png
---
To use virtual environments with jupyter notebook, best practice is to create an independent virtual environment and add it to jupyter notebook as a kernel. This provides the portability to use the same venv on other IDEs or commandline as well as remove the venv from jupyter notebook incase it is no longer required and delete the venv. Let's dive into creating and setting up a new ven on jupyter notebook in windoes system. Recommended to create and add new venvs for each python project so that each project's dependencies can be safely isolated from others to avoid conflicts. 

Jupyter notebook handles venvs as kernels. These kernels can be added to existing jupyter notebook by installing ipykernel library on venv and installing the venv as new kernel to existing jupyter notebook installation. Follow the steps below by updating the command format as per your OS and commandline.


# OBJECTIVE
1. Create & activate New Virtual Environment on Windows local system using virtualenv wrapper
3. Add Virtual Environment Kernel to jupyter notebook
4. Activate New virtual environment Kernel in jupyterbook using 'Change Kernel'
5. Remove/Delete a kernel from jupyter notebook


## 1. CREATE & ACTIVATE NEW VIRTUAL ENVIRONMENT ON WINDOWS SYSTEM

**NOTE:** All commands are based on Windows PowerShell 2. Please follow the steps by changing command formats accordingly for your commandline tool and OS.

### Navigate to directory where you new virtual environment is to be created
```
cd Replace_this_with\path_to_directory\for_new_venv\
```
### Create new folder where environment will be saved such as venv_project_name
```
mkdir venv_NEW_DIRECTORY_NAME
```
### Navigate into new directory
```
cd .\venv_NEW_DIRECTORY_NAME\
```

### Create New Virtual Environment Using Virtualenv Wrapper
- Choose Any Suitable Virtual Environment Name Such As virtual_env_name 
- Providing path to python installation is optional. Use any one command below:
```
virtualenv virtual_env_name
virtualenv virtual_env_name -p C:/ProgramData/Anaconda3/python.exe
```

### Activate New Virtual Environment
```
./virtual_env_name/Scripts/activate
```

## 2. ADD VIRTUAL ENVIRONMENT KERNEL TO JUPYTER NOTEBOOK

### Intsall `ipykernel` in New Virtual Environment
```
pip install ipykernel
```

### Add New Venv as ipykernel to Jupyter Notebook & list all ipykernels
```
python -m ipykernel install --name=virtual_env_name
jupyter kernelspec list
```

## 3. ACTIVATE NEW VIRUAL ENVIRONMENT OR KERNEL IN JUPYTER NOTEBOOK
- Launch jupyter notebook through commandline using `jupyter notebook` command
- Open a new notebook
- Alternatively, if jupyter notebook is already running then refresh/reload browser
- In the Menu bar navigate to Kernel --> Change Kernel --> Select virtual_env_name (name of the newly created and added virtual environment)
- Observe Kernel name on the top right change from `Python 3` to `virtual_env_name`

### Congrats! New Virtual Environment Kernel is now actiavted in Jupyter notebook

- For using an existing kernel already added to jupyter notebook only navigate to Kernel --> Change Kernel --> Select virtual_env_name
- There is no need to activate virtual environment in command prompt or terminal to use the kernel in jupyter notebook. The terminal for jupyter notebook will shutdown the running `Python 3` Kernel and activated the selected `virtual_env_name` kernel
- To install pip packages activate virtual environment on commandline and install packages using `pip install package_name` as usual on commandline

## 4. DELETE KERNEL FROM JUPYTER NOTEBOOK

### List all kernels to copy name of kernel to be removed
```
jupyter kernelspec list
```
### Remove kernel using `unistall`
```
jupyter kernelspec uninstall unwanted_kernel_name
```