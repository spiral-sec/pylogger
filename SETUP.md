# Setup

## Clone the project
```sh
git clone git@github.com:bogdzn/pylogger.git && cd ./pylogger/
```
## Setup a virtual environment

### Installation

In order to have the exact same dependencies as the ones in the `pylogger` and `pyserver` files,
you should install a virtual environment and download the dependencies with their specific versions
mentioned in the `requirements.txt`.

First, install [pip3](), the official package manager of python :

### Fedora
```shell
sudo dnf install python3-pip
```

### Ubuntu
```shell
sudo apt install python3-pip
```
Then from this package manager, you can install `virtualenv` like so:

```shell
pip3 install virtualenv
```

### Build
Now you can build your `virtualenv` in the current folder :
```shell
virtualenv venv
```
> :bulb: Here, we name our `virtualenv` folder `venv`, but you could have given any other name.

And to activate it :

```shell
. venv/bin/source/activate
```
Your shell should notify you that you are now in `venv`. All the python dependencies that you will download
will only be stored in the `venv` folder, not in your machine. It avoids you to have a lot of python librairies
you will only use once.

Finally, to download the project dependencies :

```shell
(venv) $ pip3 install -r requirements.txt
```

And that is it !

[Go back to the exercice](./README.md)
