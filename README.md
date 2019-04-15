# pipenv-analysis-startup
:penguin: Example of managing IPython, Jupyter, matplotlib custom configs in a Pipenv's environment

This repository demonstrates how to manage custom IPython profile, Jupyter kernel, and matplotlib rc/style in a [pipenv](https://pipenv.readthedocs.io/en/latest/)'s environment using [pipenv-analysis-configs].
Pipenv and other virtual environment tools are useful to create an independent Python environment, however, they (of course) don't manage configs of third-party Python packages within the environment.
[pipenv-analysis-configs] is series of shell scripts to create such configs within the environment, independent of *default* configs usually installed under your home directory.
This repository makes use of [pipenv-analysis-configs] as a submodule (etc) to demonstrate the usage of it.
It also hosts pipenv files (Pipfile, Pipfile.lock) as examples so that you can start to setup a Python environment for some data analysis.

[pipenv-analysis-configs]: https://github.com/astropenguin/pipenv-analysis-configs

## Usage

This will create a Python 3.7 environment including IPython, Jupyter, NumPy, pandas, and matplotlib.
It also create environment-tied IPython profile, Jupyter kernel, matplotlib rc/style in the project directory.

```shell
$ git clone --recursive https://github.com/astropenguin/pipenv-analysis-startup.git
$ cd pipenv-analysis-startup
$ pipenv install
$ etc/configure
```

## References

+ [astropenguin/pipenv-analysis-configs -- Create IPython, Jupyter, matplotlib custom configs in a Pipenv's environment](https://github.com/astropenguin/pipenv-analysis-configs)
+ [Overview of the IPython configuration system — IPython documentation](https://ipython.readthedocs.io/en/stable/development/config.html)
+ [Installing the IPython kernel -- IPython documentation](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)
+ [Custom Script Shortcuts — pipenv documentation](https://pipenv.readthedocs.io/en/latest/advanced/#custom-script-shortcuts)
+ [Automatic Loading of .env -- pipenv documentation](https://pipenv.readthedocs.io/en/latest/advanced/#automatic-loading-of-env)
