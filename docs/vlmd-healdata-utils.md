# How to Generate HEAL-compliant Data Dictionaries

In order to submit a study’s data dictionary to the Platform, the data dictionary must conform to the HEAL [variable-level metadata schema](https://github.com/HEAL/heal-metadata-schemas/tree/variable-level-metadata/variable-level-metadata-schema). The following instructions will demonstrate how to use a tool we’ve created (called the **HEAL Data Utilities**) to help you make your existing data dictionary HEAL-compliant.

##  Getting Started 

The HEAL Data Utilities is a software package that can be leveraged via a **command-line interface**. If you already have experience with the command-line interface, please see [our instructions for advanced users](#3-install-the-heal-data-utilities).

### The Command-line Interface (CLI)

To get started, you will need to navigate to your computer’s **command-line interface**, or CLI. On macOS, this is known as **Terminal**. For Windows and PC users, your command-line interface may be **PowerShell** or **Command Prompt**. 


### Python

The HEAL Data Utilities is built on Python, a widely used programming language that may   already be installed on your computer.

While the HEAL Data Utilities should be compatible with most versions of Python, you can download the latest version of Python [here](https://www.python.org/downloads/)

Once you have opened the command-line interface, you can now begin following the steps outlined below. 

## 2. Set Up a Virtual Environment

We highly recommend installing the HEAL Data Utilities in a virtual environment, since there are several software dependencies that will be installed along with `healdata-utils`. A virtual environment will allow you to successfully install these packages without affecting other software already installed on your computer. The following steps will walk you through this process. You can learn more about creating virtual environments with Python [here](https://docs.python.org/3/library/venv.html).  

!!! info
     If you are already proficient in setting up virtual environments, we recommend that you follow your usual protocol. The following instructions are for those with less familiarity with the CLI and virtual environemnts. Please jump ahead to the [installation instructions](#3-install-the-heal-data-utilities). 

### Create a Project Folder

![](../img/create_project_folder.gif)

- `mkdir my_project/`

- `cd my_project `

These two lines create a folder, or directory, named my_project. That folder is then set as the current working directory; this directory will become the virtual environment. 

### Create Input and Output Folders

![](../img/create_inputoutput.gif)

- `mkdir input`

- `mkdir output`

These two lines create:

- an input folder, where you will download your study’s data dictionary; and

 - an output folder, where your generated HEAL-compliant data dictionary will be saved.

### Download Your Study’s Data Dictionary

There are many applications and software packages that are commonly used during the data collection and processing phases of studies. The HEAL Data Utilities accommodates ten different input file formats, which include:

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

#### MacOS and Linux

`source venv/bin/activate`

#### Windows and PC

`venv\Scripts\activate.bat`

If you would like to deactivate your virtual environment at any time, use the command `deactivate`.

## 3. Install the HEAL Data Utilities 

Now that you’ve created and activated your virtual environment, you can install the HEAL Data Utilities. 

`pip install healdata-utils`

Next, to confirm that the HEAL Data Utilities package was installed correctly:

`which vlmd`

The installation path should look like something like this:

`/Users/my_username/path_to_project_folder/my_project/venv/bin/vlmd`

## 4. Generate a HEAL Data Dictionary 

Now that the HEAL Data Utilities python package has been successfully installed, it can be used to generate a HEAL-compliant data dictionary. The command `vlmd` will be used to call the healdata-utils python package. 

To confirm installation and to see the different command options:

`vlmd --help`

![](../img/vlmd_options.png)

Note that the only required flag is `--filepath`, the path to the file you want to convert to a HEAL data dictionary. 

---

Here is how you would generate a HEAL Data Dictionary with a data dictionary downloaded from RedCap:

#### MacOS and Linux

Execute the following command: 

`vlmd --filepath ./input/example_redcap_demo.redcap.csv --inputtype redcap.csv --outputdir ./output/heal-vlmd-from-redcap.csv`

#### Windows and PC

Execute the following command: 

`vlmd --filepath .\input\example_redcap_demo.redcap.csv --inputtype redcap.csv --outputdir .\output\heal-vlmd-from-redcap.csv`

In this command, `example_repcap_demo.redcap.csv` is the filename of the data dictionary that was exported from RedCap, `redcap.csv` is the file type of the inputted data dictionary, and heal-vlmd-from-redcap.csv is the filename chosen for the newly created HEAL-compliant data dictionary. 

Once this command executes, the generated HEAL-compliant data dictionary can be found in the `/output/` folder.

If you do not enter a `--description`, it will produce an error for the JSON format: 

`JSON data dictionary not valid, see heal-json-errors.json`

---

## Summary of Command Line Prompts

1. `mkdir my_project`
2. `cd my_project`
3. `python -m venv venv`
4. Activate your virtual environment
`source venv/bin/activate` or `venv\Scripts\activate.bat`
5. `mkdir input`
6. `mkdir output`
7. Download Your Data Dictionary into the `my_project/input/` folder
8. `pip install healdata-utils`
9. `vlmd --help`
10. `vlmd --filepath ./input/example_redcap_demo.redcap.csv --inputtype redcap.csv --outputdir ./output/heal-vlmd-from-redcap.csv`
