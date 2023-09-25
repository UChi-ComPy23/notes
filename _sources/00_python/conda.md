# Installing Anaconda Python

In this course, we'll support the use of the Anaconda Python distribution.

You are welcome to use some other setup (e.g. system Python), but you'll be on your own for troubleshooting.

## Download and Install Miniconda

You can choose between:
1. A [full Anaconda Python distribution](https://www.anaconda.com/products/individual)
2. A [Miniconda distribution](https://docs.conda.io/en/latest/miniconda.html)

You will only need what is in Miniconda - Anaconda includes a variety of additional bells and whistles that you might find appealing, but we won't make use of them in this course.

Installation will depend on your operating system.  We'll assume that this goes smoothly.

### Installing Miniconda on Linux

As per the Miniconda instructions, you can install Miniconda on a Linux machine using the following commands.

```bash
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh

~/miniconda3/bin/conda init bash
```

### Installing Miniconda on macOs

As per the Miniconda instructions, you can install Miniconda on a mac using the following commands.

```bash
mkdir -p ~/miniconda3
curl https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh

~/miniconda3/bin/conda init bash
```

### Installing Miniconda on Windows

Install [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) and then see above instructions.

Typically, you can install WSL quite easily by typing `wsl --install` into Windows Powershell.

### Testing installation
You should be able to open up a terminal, and type
```bash
$ which python
```
and see something like
```
~/miniconda3/bin/python
```

You can also launch a Python interpreter, which should tell you it is an Anaconda distribution:
```bash
$ python
```
This will launch a Python REPL:
```
Python 3.7.7 (default, May  7 2020, 21:25:33)
[GCC 7.3.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
type `exit()`, or type `ctrl+d` to exit.

You should also have a command called `conda` available
```bash
$ conda --version
```
Should return
```
conda 4.8.4
```
(or some similar version)

## Create an environment

The first thing you'll want to do is create an environment for this course.

You can also create environments for other courses, research projects etc.  Each environment can have different versions of everything - this makes dependency management easy.

We'll call our environment `pycourse`.  Make sure you specify Python 3.8 in the creation of the environment.

```bash
$ conda create -n pycourse python=3.8
```
You can then activate your environment using
```bash
$ conda activate pycourse
```
You will probably see a change in your command prompt to
```bash
(pycourse) $
```

### Testing your setup

If you are in your `pycourse` environment, you should see you have a new path to Python, and

```bash
(pycourse) $ which python
~/miniconda3/envs/pycourse/bin/python

(pycourse) $ python --version
Python 3.8.3
```

## Install packages

You can also use the `conda` command to install some packages.  Let's start with

```bash
(pycourse) $ conda install ipython numpy scipy sympy matplotlib
```
This will then print a variety of information.  You should see a prompt
```
Proceed ([y]/n)?
```
hit `y` and press `enter` to finish installation.

### Test your installation

You should now have a new command called `ipython`, which is an enhanced version of Python

```bash
(pycourse) $ which ipython
~/miniconda3/envs/pycourse/bin/ipython
```

Launch `ipython`:
```bash
(pycourse) $ ipython
Python 3.8.3 (default, Jul  2 2020, 16:21:59)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.18.1 -- An enhanced Interactive Python. Type '?' for help.

In [1]:      
```

Now try importing a package (hit enter at the end of each line)
```ipython
In [1]: import numpy as np                                                      

In [2]: a = np.array([1,2,3])                                                   

In [3]: a                                                                       
Out[3]: array([1, 2, 3])

In [4]: exit()  
```
