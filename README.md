# pipenv-ipython-jupyter
:penguin: IPython and Jupyter configs' management in a Python-Pipenv

This repository demonstrates how to manage a IPython profile and a Jupyter kernel in a Python virtual environment made by Pipenv.

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
This is because it uses the `IPYTHONDIR` environment variable.
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

## An example: Pipenv custom script

The setup described above can be automated by creating a script and runnning by Pipenv's custom script.
This repository has etc/configure as the script and you can run it like:

```shell
$ git clone https://github.com/astropenguin/pipenv-ipython-jupyter.git
$ cd pipenv-ipython-jupyter
$ pipenv install
$ pipenv run configure
```