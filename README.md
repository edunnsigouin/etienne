I need to use uv instead of conda for security reasons when working on a tryg VM. Below are instructions for how to set up a self contained python project.

starting a python project:
``` bash
uv init 'project_name'
```

# create a virtual environment + install package. Virtual environment is created automatically within the project when using 'uv add':
cd ./project_name
uv add 'package_name'
# note that virtual environment is called the same as the project name.

# activate virtual environment
source  .venv/bin/activate

# deactivate virtual environment
deactivate

# check list of packages in virtual environment
uv pip list (or check pyproject.toml)

# To install own code as a package, create directory with code to install
mkdir ./project_name/src/project_name
touch __init__.py

# open pyproject.toml and add following lines
name = "project_name"
include = ["src"]
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

# install own code as package
uv sync

# everything should be good to go!
