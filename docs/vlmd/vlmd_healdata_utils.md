# Generate a HEAL-compliant Data Dictionary (Beta Testing)

!!! info

    The following instructions will walk you through the process of downloading a stand-alone executable version of the VLMD Tool. This is recommended for users with less familiarity with the CLI, who want a more streamlined approach to generate HEAL-compliant data dictionaries. If you would like to install and integrate the VLMD Tool into an existing local pipeline, please check out the HEAL Data Utilities on [GitHub](https://github.com/heal/healdata-utils) or [PyPi](https://pypi.org/project/healdata-utils/) for more information.

The HEAL Data Utilities is a tool developed in order to help investigators generate HEAL-compliant variable-level metadata (VLMD), in the form of standardized data dictionaries. This VLMD Tool is a software package that can be leveraged via a command-line interface (CLI) and HEAL Workspaces, and it can also be incorporated into existing pipelines. 

There are many applications and software packages that are commonly used during the data collection and processing phases of studies. The HEAL Data Utilities accommodates several different input file formats. Please follow the links below if you would like to learn more:

- [CSV datasets](https://heal.github.io/healdata-utils/vlmd/extract/csvdata){:target="_blank"}
- [CSV (minimal) data dictionary](https://heal.github.io/healdata-utils/vlmd/extract/csvdd){:target="_blank"}
- [SPSS datasets](https://heal.github.io/healdata-utils/vlmd/extract/spss){:target="_blank"}
- [SAS datasets](https://heal.github.io/healdata-utils/vlmd/extract/sas){:target="_blank"}
- [Stata datasets](https://heal.github.io/healdata-utils/vlmd/extract/stata){:target="_blank"}
- [REDCap data dictionary](https://heal.github.io/healdata-utils/vlmd/extract/redcapcsv){:target="_blank"}
- [Frictionless Table Schema](https://heal.github.io/healdata-utils/vlmd/extract/frictionlessschema){:target="_blank"}
- [Excel dataset](https://heal.github.io/healdata-utils/vlmd/extract/exceldata){:target="_blank"}

---

## Using the Stand-alone VLMD Tool

In an effort to further streamline the data dictionary extraction process for researchers, we have developed a stand-alone executable version of the VLMD Tool. 

!!! info "Download the VLMD Tool"
   
    You can download the latest version of the VLMD Tool for your operating system (i.e., MacOS, Windows, Linux) from the NIH HEAL Initiative’s GitHub repository:

    <p align="center">[Download Latest Software Release](https://github.com/HEAL/healdata-utils/releases/latest){ .md-button }</p>

Once you have downloaded the zip file, double-click the file to unzip the package. You should then see a file labeled `vlmd` or `vlmd.exe`, depending on your operating system. 

Double-clicking `vlmd` will then open your computer's command-line interface (CLI). Once the interface opens and the VLMD Tool is loaded, you will be presented with four options: documentation, extract, start, and validate. 

![](../img/vlmd_interface.gif)

### CLI Commands 

#### extract
:Extract the variable level metadata from an existing file with a specific type/format

#### start
Start a data dictionary from an empty template

#### validate 
Check (validate) an existing HEAL Data Dictionary file to see if it follows the HEAL specifications after filling out a template or further annotation after extracting from a different format.

!!! info

    Typing the `documentation` command will launch the VLMD Data Dictionary definitions in the [HEAL Data Utilities documentation](https://heal.github.io/healdata-utils/vlmd/#csv-and-json-data-dictionary-definitions).

---

## Using the VLMD Tool in HEAL Workspaces with Python

The VLMD Tool can also be leveraged in HEAL workspaces, rather than downloading to your local machine. To request access to a workspace, see instructions [here](./heal_workspace_registration.md).

Once workspace access has been approved, select the **(Generic) Jupyter Lab Notebook with R Kernel** to get started using the VLMD Tool.

![](../img/generic_workspace_image.png){ height=500 }

After you’ve launched the workspace, you can import the necessary functions. The below commands provide examples of how to extract VLMD from an SPSS data file, create a new VLMD file from scratch, and validate an existing data dictionary in CSV and JSON formats. 

### Python Functions

#### extract
```python

from healdata_utils import convert_to_vlmd

convert_to_vlmd(input_filepath="/pd/myproject/myfile.sav",inputtype="spss")

```

!!! warning 

    Currently the python subcommand is `convert_to_vlmd` but will be changed to `extract_to_vlmd` to be
    consistent with CLI. `extract` was chosen to better reflect the functionality.

#### start
```python

from healdata_utils import write_vlmd_template

write_vlmd_template(tmpdir.joinpath("heal.csv"),numfields=10)
    
```
#### validate 
```python

from healdata_utils import validate_vlmd_csv,validate_vlmd_json

validate_vlmd_csv("data/myhealcsvdd.csv")

validate_vlmd_json("data/myhealjsondd.json")

```

## Output

Both the python and command line routes will result in a JSON and CSV version of the HEAL data dictionary in the output folder along with the validation reports in the `errors` folder. See below:

### Errors

#### heal-csv-errors.json

- outputted validation report for table in csv file against frictionless schema

If valid, this file will contain:
```json
{
    "valid": true,
    "errors": []
}
```
#### heal-json-errors.json  
- outputted jsonschema validation report.

If valid, this file will contain:
```json
{
    "valid": true,
    "errors": []
}
```

If no `outputdir` specified, the resulting HEAL-compliant data dictionaries will be named:

- `heal-csvtemplate-data-dictionary.csv`: This is the CSV data dictionary
- `heal-jsontemplate-data-dictionary.json`: This is the JSON version of the data dictionary

For more information on workflows, functions, and definitions, please see the [HEAL Data Utilities Documentation](https://heal.github.io/healdata-utils/){:target="_blank"}. 

## Next Steps 

Once you’ve created your HEAL-compliant data dictionary, you’re now ready to submit your data dictionary to the Platform. Please see our instructions on submitting a data dictionary.

- [How to Submit a Data Dictionary](./vlmd_submission.md)

If you have need any help generating a HEAL-compliant data dictionary with the VMLD Tool, or have a general inquiry, please contact us at [heal-support@datacommons.io](mailto:heal-support@datacommons.io)



