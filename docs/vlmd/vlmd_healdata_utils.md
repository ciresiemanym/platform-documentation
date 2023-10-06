# Generate a HEAL-compliant Data Dictionary (Beta Testing)

The HEAL Data Utilities is a tool developed in order to help investigators generate HEAL-compliant variable-level metadata (VLMD), in the form of standardized data dictionaries. This VLMD Tool is a software package that can be leveraged via a **command-line interface** (CLI) and HEAL Workspaces, but can also be incorporated into existing pipelines. 

!!! info
  The following instructions will walk you through the process of downloading a stand-alone executable version of the VLMD Tool. This is recommended for users with less familiarity with the CLI, who want a more streamlined approach to generate HEAL-compliant data dictionaries. If you would like to install and integrate the VLMD Tool into an existing local pipeline, please check out the HEAL Data Utilities on [GitHub](https://github.com/heal/healdata-utils) or [PyPi](https://pypi.org/project/healdata-utils/) for any requirements and more information.


---

## Download the VLMD Tool

You can download the latest version of the VLMD tool from the NIH HEAL Initiative’s GitHub repository here: https://github.com/HEAL/healdata-utils/releases/latest

Please select and download the version that matches your operating system. If your computer is running MacOS, you should select ‘healdata-utils-mac.zip’; for Windows, ‘healdata-utils-windows.zip’; for Linux, ‘healdata-utils-linux.zip’.  

Once you have downloaded the zip file, double-click the file to uncompress the package. You should then see a file labeled `vlmd` or `vlmd.exe`, depending on your operating system. 

![](../img/uncompress_vlmd_tool.gif)

Double-clicking `vlmd` will open your computer's command-line interface. On macOS, this is the application **Terminal**. For Windows and PC users, your command-line interface may be **PowerShell** or **Command Prompt**.  Once the interface opens and the Tool is loaded, you will be greeted with four options: documentation, extract, start, and validate. 

![](../img/vlmd_interface.gif)

`documentation` : Launch the vlmd data dictionary definitions in the documentation

`extract`: Extract the variable level metadata from an existing file with a specific
  type/format

`start`: Start a data dictionary from an empty template

`validate`: Check (validate) an existing HEAL data dictionary file to see if it follows the HEAL specifications after filling out a template or further annotation after extracting from a different format.

---

## Useing the VLMD Tool in HEAL Workspaces 

For users who are interested in or curious about HEAL Workspaces, they now have the opportunity to use it in real time (i don’t like this sentence). Users will first have to request access to use a HEAL Workspace. Instructions can be found here (https://heal.github.io/platform-documentation/heal_workspace_registration/) 

Once you’ve been approved to use HEAL Workspaces, you can select the [whichever is the appropriate workspace image] 

<!--- [ picture of the heal workspace with VLMD tool installed — is it all of them? ]--->

Please note, using the VLMD Tool in HEAL Workspaces is only recommended for users who have input data dictionary, rather than an entire dataset. We do not recommend uploading your entire dataset into the secure cloud environment. 

