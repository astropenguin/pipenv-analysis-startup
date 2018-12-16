# pipenv-ipython-jupyter
:penguin: Demo of IPython and Jupyter configs' management in a Python-pipenv

This repository demonstrates how to manage a IPython profile and a Jupyter kernel in a Python virtual environment created by [pipenv](https://pipenv.readthedocs.io/en/latest/).

## How to setup

### Create an environment

```shell
$ mkdir env && cd env
$ pipenv --python 3
$ pipenv install ipython jupyter
$ echo 'IPYTHONDIR=.ipython' >> .env
```

First of all, create an environment by Pipenv and install Ipython and Jupyter.
Then set up an environment variable `IPYTHONDIR=.ipython` in the .env file.

### Create an IPython profile

```shell
$ pipenv shell
(env) $ mkdir -p .ipython
(env) $ ipython profile create default
```

IPython profile (profile_default) is installed under ./.ipython directory.
This is because [pipenv uses the `IPYTHONDIR` environment variable](https://pipenv.readthedocs.io/en/latest/advanced/#automatic-loading-of-env).
See `ipython profile create --help` for more details.

### Create a Jupyter kernel

```shell
$ pipenv shell
(env) $ ipython kernel install --sys-prefix --profile default --display-name Default
```

Jupyter kernel (python3) is installed under ./.venv/share/jupyter/kernels directory.
The option `--sys-prefix` is essential to install it in the environment.
It uses the IPython profile created above as a kernel's profile.
See `ipython kernel install --help` for more details.

## An example: pipenv custom script

The setup described above can be automated by creating a script and runnning it from [pipenv's custom script](https://pipenv.readthedocs.io/en/latest/advanced/#custom-script-shortcuts).
As an example, this repository has etc/configure as the script.
You can run it to configure like:

```shell
$ git clone https://github.com/astropenguin/pipenv-ipython-jupyter.git
$ cd pipenv-ipython-jupyter
$ pipenv install
$ pipenv run configure
```

If you use git, remember to add .ipython to your .gitignore.
You may still track some files by configuring it like:

```
# tracking only config and startup files.
/.ipython/profile_default/*
!/.ipython/profile_default/startup
!/.ipython/profile_default/ipython_config.py
!/.ipython/profile_default/ipython_kernel_config.py
```

## References

+ [Overview of the IPython configuration system — IPython documentation](https://ipython.readthedocs.io/en/stable/development/config.html)
+ [Installing the IPython kernel -- IPython documentation](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)
+ [Custom Script Shortcuts — pipenv documentation](https://pipenv.readthedocs.io/en/latest/advanced/#custom-script-shortcuts)
+ [Automatic Loading of .env -- pipenv documentation](https://pipenv.readthedocs.io/en/latest/advanced/#automatic-loading-of-env)