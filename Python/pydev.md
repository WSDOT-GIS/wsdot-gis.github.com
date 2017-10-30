Python Development
==================

**This guide is currently a work-in-progress.**

Python is mainly used at WSDOT in association with ArcGIS software.

Recommendations
---------------

Write Python code to work with both Python 2.x and Python 3.x by [following these guidelines][Porting Python 2 Code to Python 3]. The list below shows which software uses which version of Python.

* Python 2.X
    * 32-bit
        * ArcGIS Desktop
    * 64-bit
        * ArcGIS Desktop ([Background Geoprocessing])
        * ArcGIS Server
* Python 3.X (64-bit)
    * ArcGIS Pro

Include the following line to force Python 2.x to behave like Python 3.x.

```python
from __future__ import absolute_import, division, print_function, unicode_literals
```


Use [argparse] module when creating command-line tools. If your module contains a script called `__main__.py` then it can be run from the console using `python -m`.

Recommended Tools
-----------------

* [Visual Studio Code]
    * [Python Extension]
    * [gitignore extension] - Used for easily creating a `.gitignore` file for Python development.

### Tools installed as Python packages ###

These tools can be installed via [pip]. Alternatively, some can also be installed via [Conda].

* [pylint]
* [autopep8]

Starting a new project
----------------------

1. Create a new folder.
2. Open the folder in Visual Studio Code.
3. From the Command Pallette, select *Add gitignore* and then *Python* to generate a new `.gitignore` file.
4. Set up the folder structure described in *[Extending geoprocessing through Python modules]*.

Pylint configuration
--------------------

Pylint will not recognize some arcpy classes or properties and you will need to modify the `generated-members` section of your `.pylintrc` file. ([Examples][generated members example])

Links
-----

* [WSDOT Python projects on GitHub]
* [Extending geoprocessing through Python modules]
* [Python Packaging User Guide]

[argparse]:https://docs.python.org/3/library/argparse.html
[autopep8]:https://pypi.io/project/autopep8/
[Background Geoprocessing]:https://desktop.arcgis.com/en/arcmap/latest/analyze/executing-tools/64bit-background.htm
[Conda]:http://pro.arcgis.com/en/pro-app/arcpy/get-started/using-conda-with-arcgis-pro.htm
[Extending geoprocessing through Python modules]:https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/extending-geoprocessing-through-python-modules.htm
[generated members example]:https://github.com/search?utf8=%E2%9C%93&q=org%3AWSDOT-GIS+filename%3A.pylintrc+generated-members&type=Code
[gitignore extension]:https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore
[pip]:https://pip.pypa.io/
[Porting Python 2 Code to Python 3]:https://docs.python.org/3/howto/pyporting.html
[pylint]:https://pypi.io/project/pylint/
[Python Extension]:https://marketplace.visualstudio.com/items?itemName=donjayamanne.python
[Python Packaging User Guide]:https://packaging.python.org/
[Visual Studio Code]:https://code.visualstudio.com/
[WSDOT Python projects on GitHub]:https://github.com/WSDOT-GIS?utf8=%E2%9C%93&q=&type=&language=python
