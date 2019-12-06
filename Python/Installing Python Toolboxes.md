# Installing Python Toolboxes

This is a guide to installing custom Python packages that include [Python Toolboxes][what is a python toolbox?]. This guide is meant for packages built with the folder structure described in [Extending geoprocessing through Python modules].

This guide uses [pip] to install Python packages. The [pip] command retrieves packages from the [Python Package Index], pypi.org.

## Installing a package

To install the `wsdottraffic` package for the current user, use the following command. When installing a different package, use that package name instead of `wsdottraffic`.

```
pip install wsdottraffic --user
```

To install the package for **all users**, simply omit the `--user` argument from the above command.

## Adding additional package hosting site

By default, [pip] will only search pypi.org for packages. Once the steps below have been completed, you will be able to use the `pip install` command to install packages for sites other than pypi.org. (See [Hosting your own simple repository] for details on how to set up your own repository.)

1. Open the `%allusersprofile%` folder, then open the `pip` subfolder, or create it if it does not already exist.
2. Open the `pip.ini` file in a text editor, first creating the file if it does not already exist.

   If the `pip.ini` file does not exist, you can create it with the following PowerShell command. This command will also generate the parent `pip` folder if necessary.

   ```PowerShell
   New-Item "$env:ALLUSERSPROFILE\pip\pip.ini" -Force
   ```

3. Add the following to the `pip.ini` file

   Replace the example URL with your own.

   ```ini
   [global]
   extra-index-url = https://example.com/PythonPackages/
   ```

   If you try to install a package from the URL and receive error messages related to HTTPS, you can work around this issue by configuring the site to be a "trusted host":

   ```ini
   [global]
   extra-index-url = https://example.com/PythonPackages/
   trusted-host = example.com
   ```

## Locating Python Toolboxes

This section will tell you where to find Python toolboxes that have been installed as part of a package installed with [pip].

### Per-user installs

You can list all of the Python Toolboxes installed for the current user account with the following PowerShell command.

```PowerShell
Get-ChildItem $env:appdata\Python\**\*.pyt -Recurse | Select-Object -ExpandProperty FullName
```

For packages installed via Conda instead of [pip].

```PowerShell
Get-ChildItem "$env:LOCALAPPDATA\ESRI\conda\**\*.pyt" -Recurse
```

### For all users installs

#### ArcGIS Desktop

```PowerShell
Get-ChildItem "$env:SystemDrive\Python*\ArcGIS*\Lib\site-packages\**\*.pyt" -Recurse
```

[extending geoprocessing through python modules]: https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/extending-geoprocessing-through-python-modules.htm
[hosting your own simple repository]: https://packaging.python.org/guides/hosting-your-own-index/
[pip]: pip.pypa.io
[python package index]: pypi.org
[what is a python toolbox?]: https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/a-quick-tour-of-python-toolboxes.htm
[wsdot-route-gp releases]: https://github.com/WSDOT-GIS/wsdot-route-gp/releases
