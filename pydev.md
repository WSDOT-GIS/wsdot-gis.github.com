Python Development
==================

Python is mainly used at WSDOT in association with ArcGIS software.

Recommendations
---------------

Write Python code to work with both Python 2.x and Python 3.x by [following these guidelines](https://docs.python.org/3/howto/pyporting.html). The list below shows which software uses which version of Python.

* Python 2.X
    * 32-bit
        * ArcGIS Desktop
    * 64-bit
        * ArcGIS Desktop ([Background Geoprocessing])
        * ArcGIS Server
* Python 3.X (64-bit)
    * ArcGIS Pro

Use [argparse] module when creating command-line tools.

Recommended Tools
-----------------

* [Visual Studio Code]
* [Python Extension] for Visual Studio Code

### Tools installed as Python packages ###

These tools can be installed via [pip]. Alternatively, some can also be installed via [Conda].

* [pylint]
* [autopep8]

[argparse]:https://docs.python.org/3/library/argparse.html
[autopep8]:https://pypi.io/project/autopep8/
[Background Geoprocessing]:https://desktop.arcgis.com/en/arcmap/latest/analyze/executing-tools/64bit-background.htm
[Conda]:http://pro.arcgis.com/en/pro-app/arcpy/get-started/using-conda-with-arcgis-pro.htm
[pip]:https://pip.pypa.io/
[pylint]:https://pypi.io/project/pylint/
[Python Extension]:https://marketplace.visualstudio.com/items?itemName=donjayamanne.python
[Visual Studio Code]:https://code.visualstudio.com/