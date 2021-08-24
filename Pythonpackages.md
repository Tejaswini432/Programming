# Packages in Python

**Package** is a collection of modules and module is a file that contain python statements and definitions.
If many modules are included ina an application, as the number of modules grows, it becomes difficult to keep track of them all if they are dumped into one location. This is particularly so if they have similar names or functionality. You might wish for a means of grouping and organizing them.

A package is basically a directory with Python files and a file with the name *__init__.py* which is mandatory to consider it as a package.This file can be left empty but we generally place the initialization code for that package in this file.

This means that every directory inside of the Python path, which contains a file named *__init__.py*, will be treated as a package by Python.

It's possible to put several modules into a Package.

A.B stands for a submodule named B in a package named A.

Two different packages like P1 and P2 can both have modules with the same name, let's say A, for example. The submodule A of the package P1 and the submodule A of the package P2 can be totally different. A package is imported like a "normal" module. 

![Alt text](https://i.pinimg.com/564x/2b/3d/54/2b3d54436921ef98a68dcbc505bf9692.jpg)

## ***Few of the most used and useful python packages:***

Despite the many different use cases for programming in Python, there are several packages that are especially useful above all. Regardless of whether you’re using Python for ML or web apps, the following packages are worth knowing and can only improve your experience with using Python.

1. **pip**: It is the standard way of installing and managing packages in Python. Pip comes standard with every Python distribution, allowing you to accomplish installs, uninstalls, updates, etc from the command line. For example, to install a specific package with pip from PyPI(the server that hosts all the public python packages that we all use), run:

pip install “SomePackage”
 
Or for a specific package version:

pip install “SomePackage == 1.0”
 
pip allows for installation from multiple sources, and is not limited to installing packages maintained on the PyPI. For more information, see the documentation here.

2. **Six**: It is a Python 2 and 3 compatibility library, which is especially relevant given the amount of application migration from Python 2 to 3 organizations are currently undertaking due to Python 2’s end of life. Six reconciles the differences between Python 2 and 3, and makes adjustments based on which version is running locally. This allows Python programmers to write code that is compatible with both versions of Python, without too much difficulty. 

For example, in Python 3, iterating dictionary keys is done by:

for item in dictionary.items():
#do something
 

In Python 2, iteration is done by:

for item in dictionary.iteritems():
#do something
 

With Six, the syntax is:

import six
for item in six.iteritems(dictionary):
#do something
 

This code will successfully run on both Python 2 and 3. 

3. **python-dateutil**: The dateutil module provides a number of date and time manipulation capabilities, such as computing relative differences between two arbitrary dates, parsing datetime objects, and handling time zone information. It builds on the datetime module that is built into Python, and is simple and easy to use. 

For example, to get the current local time:

from datetime import *
from dateutil.relativedelta import *
now = datetime.now()
 

To add an arbitrary number of months, days, and hours:

now + relativedelta(months=1, weeks=1, hour=10)
 

Or to query when the next Wednesday will occur:

now + relativedelta(weekday=WE(+1))
 

The general functionality follows this trend. The package is simple, but can dramatically improve your Python experience when handling time-series data. 

4. **Requests**: The requests package is an HTTP library for Python. It is built on top of urllib3 (another HTTP client for Python), but has a much simpler and more elegant syntax. It also integrates a few other Python libraries in order to maximize functionality while still managing to minimize complexity. Using urllib3 alone (or the built-in urllib and urllib2) allows for more customization and deeper control, but also requires more work on the side of the user. For this reason, requests is the preferred HTTP client for nearly all use cases in Python. 

For example, here’s how to make a request to Spotify:

import requests
r = requests.get(‘https://api.spotify.com/’)
r.status_code

A status code in the 200’s indicates a success. From here we can extract the headers, the encoding, and a myriad of other information:

print(r.headers)
print(r.encoding)

5. **Docutils**: The Documentation Utilities project exists to create a set of tools to easily process plaintext documents into more useful file formats such as HTML, XMS, or LaTeX. The project developed several front-end tools for the most common processes. This involves reading the input file (Reader tool), parsing appropriately (Parser tool), and writing the new file (Writer tool). The command line syntax for each of these tools follows a standard structure:

toolname [options] [<source> [<destination]]
 
Docutils is a simple utility package with limited functionality; but necessary, considering the standard Python library does not provide any code with these capabilities.      

6. Pytest: Testing code fidelity is not only good practice as a programmer, but is also made easy with pytest. The pytest package provides a framework to easily find bugs at any scale. It allows for parallel testing, autodetection of test functions or modules, subset testing, and other customizable features. 
 
7. NumPy: NumPy is the essential package for scientific and mathematical computing in Python. It introduces n-dimensional arrays and matrices, which are necessary when performing sophisticated mathematical operations. It contains functions that perform basic operations on arrays, such as sorting, shaping, and other mathematical matrix operations. 

For example, to create two 2×2 complex matrices and print the sum: 
import numpy as np

a = np.array([[1+2j, 2+1j], [3, 4]])
b = np.array([[5, 6+6j], [7, 8+4j]])
print(a+b)
 

And to take the complex conjugate of one of them:

np.conj(a)

8. Pandas: The pandas package introduces a novel data structure, the DataFrame, optimized for tabular, multidimensional, and heterogeneous data. Once your data has been converted to this format, the package provides intuitive and practical means to clean and manipulate it. 

Manipulations such as groupby, join, merge, concatenate data or filling, replacing and imputing null values can be executed in a single line. The developers of the package have the primary goal of producing the world’s most powerful data analysis and manipulation tool that exists in any language — a daunting task that they may actually achieve. 

To create a DataFrame:

import pandas as pd

df_1 = pd.DataFrame({‘col1’: [1,2], ‘col2’: [3,4]})
 

And to concatenate two dataframes together:

df_2 = pd.DataFrame({‘col3’: [5,6], ‘col4’: [7,8]})
df = pd.concat([df_1,df_2], axis = 1)
 

To perform a simple filtering operation, extracting the row that meets the logical condition:

df[df.col3 == 5]  

9. SciPy: The SciPy package builds on the NumPy package by providing functions and algorithms critical to scientific computation in technical fields. These are slightly more sophisticated than the operations built into NumPy, including algorithms for interpolation, optimization, clustering, transformation, and integration of data. These operations are essential when performing any type of data analysis, or developing ML-based models. 

To demonstrate interpolation, I first use NumPy to create some data points with an arbitrary function, then compare different interpolation methods:

from scipy.interpolate import interp1d
import pylab

x = np.linspace(0, 5, 10)
y = np.exp(x) / np.cos(np.pi * x)

f_nearest = interp1d(x, y, kind=‘nearest’)
f_linear  = interp1d(x, y)
f_cubic   = interp1d(x, y, kind=‘cubic’)

x2 = np.linspace(0, 5, 100)

pylab.plot(x, y, ‘o’, label=‘data points’)
pylab.plot(x2, f_nearest(x2), label=‘nearest’)
pylab.plot(x2, f_linear(x2), label=‘linear’)
pylab.plot(x2, f_cubic(x2), label=‘cubic’)
pylab.legend()
pylab.show()

![Alt text](https://cdn.activestate.com/wp-content/uploads/2019/12/top-10-python-packages.png)

