# Configuration Builder

## Installation

Config builder requires Python 3.8 or newer. This can be verified by pasting the following to a terminal window:
```
% python3 -c "import sys;assert sys.version_info>(3,8)" && echo "ALL GOOD"
```

If 'ALL GOOD' is printed it means Python requirements are met. If not, download and install the latest 3.x version at Python.org (https://www.python.org/downloads/).

Go to the config_builder directory and create a virtual environment
```
% cd config_builder
% python3 -m venv venv
```

Activate the virtual environment:
```
% source venv/bin/activate
(venv) %
```
- Note that the prompt is updated with the virtual environment name (venv), indicating that the virtual environment is active.
    
Upgrade built-in virtual environment packages:
```
(venv) % pip install --upgrade pip setuptools
```

Install config builder:
```
(venv) % pip install --upgrade .
```

Validate that config builder is installed:
```
(venv) % config_build --version      
Config Builder Tool Version 0.2.
```

## Running

The 'metadata.yaml' file should be in the same directory where config_build command is run. It defines the location of
the source configuration file as well as where the output files should be saved.

```
(venv) % config_build --help
usage: config_build [-h] [--version] {render,export,schema} ...

Config Builder Tool

options:
  -h, --help            show this help message and exit
  --version             show program's version number and exit

commands:
  {render,export,schema}
    render              render configuration files
    export              export source configuration as JSON file
    schema              generate source configuration JSON schema
```

To build the configuration files use render command:
```
(venv) % config_build render --update  
INFO: Rendered Ansible day_-1 vars: 'day-1_local.j2' -> '../ansible/day_-1/group_vars/all/local.yml'
INFO: Rendered Ansible day_0 vars: 'day0_local.j2' -> '../ansible/day_0/group_vars/all/local.yml'
INFO: Rendered Ansible day_1 vars: 'day1_local.j2' -> '../ansible/day_1/group_vars/all/local.yml'
```

By default, config_build will not override a target config file if it is already present. The --update (or -u) 
flag changes this behavior override any pre-existing target files.