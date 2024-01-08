![Python package](https://github.com/ReproNim/reproschema-py/workflows/Python%20package/badge.svg?branch=master)

# Reproschema Python library and Command Line Interface (CLI)

## Installation

reproschema requires Python 3.7+.

```
pip install reproschema
```

### Developer installation

To install in developer mode:

```
git clone git@github.com:ReproNim/reproschema-py.git
cd reproschema-py
pip install -e ".[dev]"
```

## CLI usage

This package installs `reproschema` a CLI.

```
$ reproschema
Usage: reproschema [OPTIONS] COMMAND [ARGS]...

  A client to support interactions with ReproSchema

  To see help for a specific command, run

  reproschema COMMAND --help     e.g. reproschema validate --help

Options:
  --version
  -l, --log-level [DEBUG|INFO|WARNING|ERROR|CRITICAL]
                                  Log level name  [default: INFO]
  --help                          Show this message and exit.

Commands:
  convert
  create
  serve
  validate
```

## redcap2reproschema Usage
The `redcap2reproschema` function is designed to process a given REDCap CSV file and YAML configuration to generate the output in the reproschema format.

### Prerequisites
Before the conversion, ensure you have the following:

**YAML Configuration File**:
   - Download [templates/redcap2rs.yaml](templates/redcap2rs.yaml) and fill it out with your protocol details.

### YAML File Configuration
In the `templates/redcap2rs.yaml` file, provide the following information:

- **protocol_name**: This is a unique identifier for your protocol. Use underscores for spaces and avoid special characters.
- **protocol_display_name**: The name that will appear in the application.
- **protocol_description**: A brief description of your protocol.

Example:
```yaml
protocol_name: "My_Protocol"
protocol_display_name: "Assessment Protocol"
protocol_description: "This protocol is for assessing cognitive skills."
```
### Command-Line Usage

The `redcap2reproschema`` function has been integrated into a CLI tool, use the following command:
```bash
reproschema redcap2reproschema path/to/your_redcap_data_dic.csv path/to/your_redcap2rs.yaml
```

### Python Function Usage

You can also use the `redcap2reproschema` function from the `reproschema-py` package in your Python code.

```python
from reproschema import redcap2reproschema

csv_path = "path-to/your_redcap_data_dic.csv"
yaml_path = "path-to/your_redcap2rs.yaml"

reproschema2redcap(input_dir_path, output_csv_filename)
```

After configuring the YAML file:

1. Run the Python script with the paths to your CSV file and the YAML file as arguments.
2. Command Format: `python script_name.py path/to/your_redcap_data_dic.csv path/to/your_redcap2rs.yaml`

### Notes
1. The script requires an active internet connection to access the GitHub repository.
2. Make sure you use `git add`, `git commit`, `git push` properly afterwards to maintain a good version control for your converted data.

## Developer installation

Install repo in developer mode:

```
git clone https://github.com/ReproNim/reproschema-py.git
cd reproschema-py
pip install -e .[dev]
```

It is also useful to install pre-commit, which takes care of styling when
committing code. When pre-commit is used you may have to run git commit twice,
since pre-commit may make additional changes to your code for styling and will
not commit these changes by default:

```
pre-commit install
```
