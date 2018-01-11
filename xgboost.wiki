# Xgboost

## Installation

https://ampersandacademy.com/tutorials/python-data-science/install-xgboost-on-mac-os-sierra-for-python-programming

Install XGBoost on Mac OS Sierra for Python Programming

First, build the shared library from the C++ codes (libxgboost.so).  Then
install the Python language packages.

1. Python(Download and install Python from python.org website)

XGBoost supports multi-threading. So you can use the multithreading feature if
you need. But enabling multi-thread feature is very high time-consuming
process. It took me to install the multi-threading library. So the choice is
yours. Try with Without multi-threading or With multi-threading.

Run the below two commands on the terminal to install the shared
library.

```
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost; cp make/minimum.mk ./config.mk; make -j4
```

That's all. You are done.


By default clang in OSX does not come with open-mp. Use the
below code for OpenMP enabled XGBoost.

Now, clone the repository
```
git clone --recursive https://github.com/dmlc/xgboost
```

Next copy the conﬁg ﬁle.
```
cd xgboost; cp make/config.mk ./config.mk
```

Now open the conﬁg.mk ﬁle using the below command or open
with any text editor.
```
vi config.mk
```

Uncomment the lines near the top of the ﬁle:
```
export CC = gcc
export CXX = g++
```

Change them to the following:
```
export CC = gcc-7
export CXX = g++-7
```

And Change them to the following in the Makeﬁle.

```
export CC = gcc-7
export CXX = g++-7
```

Save the ﬁle. Now you need to run a cleaning step since you
changed the Makeﬁle.

```
make clean_all && make -j4
```

The python package is located at python-package.
Install system-widely, which requires root permission.
```
cd python-package; sudo python setup.py install
```

That's all. Now you successfully installed the XGBoost library.
Import the XGBoost like below on Anaconda or Python.
import xgboost as xgb

Sometimes, you will encounter some error like below while using
the XGBoost on Anaconda.

Execute the below command on terminal to solve the above error.
conda install -c conda-forge xgboost=0.6a2
