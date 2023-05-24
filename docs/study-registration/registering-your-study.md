# How to Generate HEAL-compliant Data Dictionaries

In order to submit a study’sa data dictionary to the Platform, the data dictionary must conform to the HEAL variable-level metadata schema. This page will show you how to use a tool we’ve created (healdata-utils) to help you generate a HEAL-compliant data dictionary.  

!!! info
     A current version of Python will be required to run the HEAL Data Utilities (healdata-utils). 
     
     Please see our python installation instructions for more help. 


## Set Up a Virtual Environment

We highly recommend installing the HEAL Data Utilities in a virtual environment, s. Since there are several software dependencies that will be installed along with `healdata-utils`., Aa virtual environment will allowallows you to successfully install these packages without affecting other software installedalready on your computer. You can learn more about creating virtual environments with Python [here](https://docs.python.org/3/library/venv.html).  

### Create a Project Folder

<p align="center">![](../img/create_project_folder.gif)</p>

- `mkdir my_project/`

- `cd my_project `

These two lines create a folder, or directory, named my_project. That folder is then set as the current working directory; this directory will become the virtual environment. 

### Create Input and Output Folders

[](../img/create_inputoutput.gif)

     - `mkdir input`

     - `mkdir output`

These two lines create:

     - an input folder, where you will download your study’s data dictionary; and

     - an output folder, where your generated HEAL-compliant data dictionary will be saved.
### Download Your Study’s Data Dictionary

There are many applications and softwares that are used during the data collection and processing phases of studies. The HEAL Data Utilities accommodates ten different input file formats, which include:

!!! supportedinput file formats
     1. data.csv
     2. template.csv
     3. csv
     4. sav
     5. dta
     6. por
     7. sas7bdat
     8. template.json
     9. json
     10. redcap.csv 

Download your study’s data dictionary into the `my_project/input/` folder. If you would like more information on which file formats are supported, please check out here. 

### Create Virtual Environment

- `python -m venv venv –upgrade-deps`

### Activate Virtual Environment

#### For MacOS and Linux

 `source venv/bin/activate`

#### For Windows

`venv\Scripts\activate.bat`

If you would like to deactivate your virtual environment at any time, use the command `deactivate`.

## Install the HEAL Data Utilities 

Now that you’vewe’ve created and activated your virtual environment, youwe can install the HEAL Data Utilities. 

`pip install healdata-utils`

Next, to confirm that the HEAL Data Utilities package was installed correctly:

`which vlmd`

The installation path should look like something like this:

`/Users/my_username/path_to_project_folder/my_project/venv/bin/vlmd`

## Generate a HEAL Data Dictionary 

Now that the HEAL Data Utilities python package has been successfully installed, it can be used to generate a HEAL data dictionary. The command `vlmd` will be used to call the healdata-utils python package. 

To confirm installation and to see the different options:

`vlmd --help`

![](../imgs/healtdata-utils_options.png/)

Note that the only required flag is `--filepath`, the path to the file you want to convert to a HEAL data dictionary. 

Here is how you would generate a HEAL Data Dictionary with a data dictionary downloaded from RedCap:

#### For MacOS and Linux

`vlmd --filepath ./input/example_redcap_demo.redcap.csv --inputtype redcap.csv --outputdir ./output/heal-vlmd-from-redcap.csv`

#### For Windows

`vlmd --filepath .\/input\example_redcap_demo.redcap.csv --inputtype redcap.csv --outputdir .\/output\/heal-vlmd-from-redcap.csv`

If you do not enter a `--description`, it will produce an error for the JSON format: 

`JSON data dictionary not valid, see heal-json-errors.json`

title

At this point you can deactivate your virtual environment. 
---

## Summary of Command Line Prompts

1. `mkdir my_project`
2. `cd my_project`
3. `python -m venv venv`
4. Activate your virtual environment
`source venv/bin/activate` or `venv\Scripts\activate.bat`
5. `mkdir input`
6. `mkdir output`
7. Download Your Redcap.csv Data Dictionary into the `my_project/input/` folder
8. `pip install healdata-utils`
9. `vlmd --help`
10. `vlmd --filepath ./input/example_redcap_demo.redcap.csv --inputtype redcap.csv --outputdir ./output/heal-vlmd-from-redcap.csv`
