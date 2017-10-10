Installing Python Toolboxes
===========================

This is a guide to installing custom Python packages that include [Python Toolboxes][What is a Python toolbox?]. This guide is meant for packages built with the folder structure described in [Extending geoprocessing through Python modules].

Example packages
----------------

These are examples that can be used with the process outlined in this guide.

* [wsdot-route-gp][wsdot-route-gp releases]

Installing a package
--------------------

### Prerequisites ###

* For this example we'll be using a *Python Wheel* file: https://github.com/WSDOT-GIS/wsdot-route-gp/releases/download/v2.0.0-beta.2/wsdot.route-2.0.0b2-py2.py3-none-any.whl. Instructions will be for Windows 10.
* Your system path environment variable must include the directory containing the Python executable and that directory's `Scripts` subfolder.

1. Open a *Windows PowerShell* window.
2. Use the following command to install the Python package for the current user. If you want to install the package for all users, omit the `--user` argument.
    ```console
    pip install https://github.com/WSDOT-GIS/wsdot-route-gp/releases/download/v2.0.0-beta.2/wsdot.route-2.0.0b2-py2.py3-none-any.whl --user
    ```

    You should see something similar to what is shown below as the output of the command:
    ```
    Collecting wsdot.route==2.0.0b2 from https://github.com/WSDOT-GIS/wsdot-route-gp/releases/download/v2.0.0-beta.2/wsdot.route-2.0.0b2-py2.py3-none-any.whl
        Downloading https://github.com/WSDOT-GIS/wsdot-route-gp/releases/download/v2.0.0-beta.2/wsdot.route-2.0.0b2-py2.py3-none-any.whl
    Installing collected packages: wsdot.route
    Successfully installed wsdot.route-2.0.0b2
    ```
3. Locate the installed toolbox. You can list all of the Python Toolboxes installed for the current user account with the following PowerShell command.
    ```PowerShell
    Get-ChildItem $env:appdata\Python\**\*.pyt -Recurse | Select-Object -ExpandProperty FullName
    ```
4. Use Windows Explorer to copy all of the `.pyt` files and associated `.pyt.xml` files to a new location. A good location to copy to would be a subfolder of your `Documents` folder. (E.g., `C:\Users\yourusername\Documents\Custom Python Toolboxes`)


[Extending geoprocessing through Python modules]:https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/extending-geoprocessing-through-python-modules.htm
[What is a Python toolbox?]:https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/a-quick-tour-of-python-toolboxes.htm
[wsdot-route-gp releases]:https://github.com/WSDOT-GIS/wsdot-route-gp/releases