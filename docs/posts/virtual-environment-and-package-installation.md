---
date: 2024-01-17
slug: virtual-environment-and-package-installation
categories:
  - python
  - notes
---

# Virtual Environment and package installation

Notes based on the live [Ambientes virtuais e instalação de bibliotecas - Live de Python #191]((https://www.youtube.com/watch?v=naGF7EIUFp0&t=4929s))
from the youtube channel [Eduardo Mendes - @Dunossauro](https://www.youtube.com/@Dunossauro).

<!-- more -->

* Python has a large and diverse package ecosystem.
* We just install a package using `pip`, but sometimes we want to use different versions from the same package in different projects, for example.
* And, how to install and manage different package versions? It's messy:

<figure markdown>
  ![Python environment](https://imgs.xkcd.com/comics/python_environment.png)
</figure>


## PIP
* PIP stands for Pip Install Package and just installs external packages from [PyPI](https://pypi.org/).
* It gets the package, unzip it and store it in a global folder.
* Show where the python installed the package:

```py
import site
site.getsitepackages()
``` 

* To import the package, python looks inside some specific paths.
* Show the paths python looks for the packages:
  
```py
import sys
print(sys.path)
``` 

* When stored globally, two versions from the same package can't live together
* Show package details:

```
$ pip show <package-name>
``` 

* Show dependency tree:
  
```
# pip insall pipdeptree
$ pipdeptree
``` 

* Show package list:
  
```
$ pip list
``` 

* Different python packages may have the same dependency, but they depend on different versions of the shared package.

## VENV
* Virtual environment tries to isolate the environment.
* It hacks the `site-packages` creating a local environment isolated from the global one.
* It is plug-and-play from python.
* In the same project, you can have multiple virtual environments.
* Important commands:
  
```
$ python -m venv <env-name> # -m stands for module
$ source <env-name>/bin/activate
$ deactivate
```

## VENV OR VIRTUALENV?
* virtualenv is external to python, and distributed by PyPA (Python Packaging Authority).
* venv is part of the virtualenv inside python.
* virtualenv advantages:
  * It's faster;
  * New releases are independent from python releases;
  * It's extensible;
  * Code API;
  * It supports older python versions.

## requirements
* `requirements.txt` allows you to list all packages required in your application.
* Install requirements:
  
```
$ pip install -r requirements.txt
```

* `freeze` builds `requirements.txt` file automatically. However, `freeze` gets all installed packages, not only the ones you need for your project. In that way, some unnecessary packages may be written into the requirements.

```
$ pip freeze > requirements.txt
```

* Remove the package and its dependencies:

```
$ pip uninstall <package-name> # don't uninstall the package and its dependencies
$ pip install pip-autoremove
$ pip-autoremove <package-name> # uninstall the package and its dependencies
```

* Create a `requirements_dev.txt`

```title="requirements_dev.txt"
# install production libs
-r requirements.txt

# list bellow all dev packages
package_1
package_2
package_3
```

* Sometimes we need some packages to be in a specific version, mainly if that package is a sub-dependency. That's what `constaints.txt` is for. It works in any dependency tree level and constrains the package version.
* It does not overwrite the `requiments.txt` file, it just indicates whether a specific package is going to be installed, and then install it in a specific version.

```
$ pip install -r requirements.txt -c constaints.txt
```

## Other tools

* pip's friends:
  * pip-autoremove: removes the package and its dependencies;
  * pipdeptree: dependency tree.
* venv's friends:
  * virtualenvwrapper: wraps venv commands.
* python's friends:
  * pyenv: installs different python versions;
  * tox: runs tests in different python versions;
  * pipx: installs CLI tools apart from the global environment.
* Scientific world:
  * Conda: package manager just like pip; it has its repository different from PyPI; it downloads packages from other languages, like R, fortran, C, etc.
  * miniconda: python + conda;
  * anaconda: gets all the scientific world;
  * mamba: like miniconda but in C++ aiming performance.

## Future
  * `pyproject.toml`: replaces `requirements.txt` + `requirements_dev.txt` + `setup.py``
  * poetry:
    * Handles the virtual environment (venv);
    * Handles setup.py + setup.cfg;
    * Package metadata (setup.py);
    * Package installation (pip);
    * Handles package versions (`requirements.txt`);
  * flit:
    * Just like poetry.
  * pdm:
    * [PEP 582](https://peps.python.org/pep-0582/) (Python Enhancement Proposal);
    * Handles packages without the need for the virtual environment.