---
published: true
layout: post
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
source activate py35
conda install notebook ipykernel
ipython kernel install --user


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
