I need to use uv instead of conda for security reasons when working on a tryg VM. Below are instructions for how to set up a self contained python project.

Starting a python project:
``` bash
uv init 'project_name'
```

Create a virtual environment + install package. Virtual environment is created automatically within the project when using 'uv add':
``` bash
cd ./project_name
uv add 'package_name'
note that virtual environment is called the same as the project name.
```

Activate virtual environment
``` bash
source  .venv/bin/activate
``` 

Deactivate virtual environment
``` bash
deactivate
```

Check list of packages in virtual environment
``` bash
uv pip list (or check pyproject.toml)
```

To install own code as a package, create directory with code to install
``` bash
mkdir ./project_name/src/project_name
touch __init__.py
```

Open pyproject.toml and add following lines
``` bash
name = "project_name"
include = ["src"]
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"
```

Install own code as package
``` bash
uv sync
```

Everything should be good to go!
