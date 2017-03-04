---
published: true
layout: post
title: How to setup python environment
category: python
tags:
  - python
  - environment
---
## python-environment

[Manually registering kernels](http://stackoverflow.com/questions/30492623/using-both-python-2-x-and-python-3-x-in-ipython-notebook). 


Manually registering kernels

Users who do not want to use nb_conda_kernels or still use older versions of anaconda can use following steps to manually register ipython kernels.

configure the python2.7 environment:

conda create -n py27 python=2.7
source activate py27
conda install notebook ipykernel
ipython kernel install --user
configure the python3.5 environment:

conda create -n py35 python=3.5
conda create -n py34 python=3.4
source activate py34
conda install notebook ipykernel
ipython kernel install --user

http://stackoverflow.com/questions/5599872/python-windows-importerror-no-module-named-site
	
If on windows 10, this is now: 
setx PYTHONHOME "C:\Users\oldyu\Anaconda2" 
setx PYTHONPATH "C:\Users\oldyu\Anaconda2\Lib" 
setx PATH "%PYTHONHOME%;%PATH%" 

for octave 
setx OCTAVEHOME "D:\Octave\Octave-4.2.0\bin" 
setx PATH "%OCTAVEHOME%;%PATH%" 

http://www.mingw.org/wiki/Getting_Started
C:\MinGW\bin
setx MINGWHOME "C:\MinGW\bin" 
setx PATH "%MINGWHOME%;%PATH%" 


## for dynare++

setx DYNARE++HOME  "C:\dynare\4.4.3\dynare++"
setx PATH "DYNARE++HOME;%PATH%" 


## for gurobi

setx GRB_LICENSE_FILE "e:\gurobi\gurobi.lic" 
setx PATH "%GRB_LICENSE_FILE%;%PATH%" 


python setup.py build --compiler=C:\MinGW\bin\mingw32


C:\Users\oldyu\Anaconda2

source activate py27

activate py27 : windows
deactivate 


pip install -U -r requirements.txt 

(-U = update if it had already installed)


[Managing environments](http://conda.pydata.org/docs/using/envs.html)


for example:

$ virtualenv3 nikola
Note:
  The command might be different in some environments.
  You might need to use one of the following instead:
    virtualenv
    virtualenv-3.x (where x is your Python version)
    virtualenv -p /usr/bin/python3

Using base prefix '/usr'
New python executable in nikola/bin/python3
Also creating executable in nikola/bin/python
Installing setuptools, pip, wheel...done.
$ cd nikola
$ source bin/activate
$ pip install --upgrade "Nikola[extras]"
...snip...
Successfully installed Nikola

 virtualenv3 is obsolete!

Thanks to the hard work of the core virtualenv team, the main virtualenv package has gained native support for Python 3, so ad-hoc forks of the program like this one are no longer necessary. From this time forward, you can simply download the mainline virtualenv and install it using your Python 3 interpreter.

virtualenv -p python3 envname

in my case. only works on ubuntu
virtualenv nikola
cd Scripts
activate nikola
pip install --ignore-installed   --upgrade "Nikola[extras]"
