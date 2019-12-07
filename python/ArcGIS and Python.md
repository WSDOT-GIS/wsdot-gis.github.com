---
title: ArcGIS and Python
layout: page
permalink: /python/arcgis/
---

It is recommended to use ArcGIS Pro for new development unless there is a specific need to use Desktop for a feature that is not available in Pro. Desktop uses Python 2.7, which is **no longer supported as of January 2020**.

## ArcGIS Pro

Please familiarize yourself with the [ArcGIS Pro Python Reference] section of the ArcGIS Pro documentation.

ArcGIS Pro uses Python 3.6 as of version 2.4.

- The [dataclasses] module was not added until Python 3.7. If you want to use [dataclasses] with an ArcGIS Pro script you will need to include [dataclasses from pypi] as a dependency of your module in the `setup.py` file.

### Conda Environments

ArcGIS Pro uses Conda to manage multiple environments, as documented in [ArcGIS Pro and Conda].

### File locations

This section describes where various files related to ArcGIS Pro's Python installation can be found. The text surrounded by percent signs (`%`) are environment variables.

| Description                                  | Location                                                          |
| -------------------------------------------- | ----------------------------------------------------------------- |
| Default Conda environment (Python EXE, etc.) | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\envs\arcgispro-py3`         |
| Conda and batch files                        | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\Scripts`                    |
| All users' scripts folder                    | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\Scripts` |
| Per-user scripts folder (installed via pip)  | `%APPDATA%\Python\Python`_36_`\Scripts` ¹                         |
| Custom Conda environments                    | `%LOCALAPPDATA%\ESRI\conda\envs\`_your-env-name_                  |
| Scripts installed via Conda                  | `%LOCALAPPDATA%\ESRI\conda\envs\`_your-env-name_`\Scripts`        |

¹ The number after the word Python may differ depending on the version of ArcGIS Pro installed. ArcGIS Pro 2.4 comes with Python 3.6, so the folder name is `Python36`.

#### Useful commands

All commands are for PowerShell unless otherwise noted.

##### Add a folder to the system path

```PowerShell
$env:Path += ";$env:PROGRAMFILES\ArcGIS\Pro\bin\Python\Scripts"
```

Windows Batch File equivalent

```batch
SET PATH=%PATH%;%PROGRAMFILES%\ArcGIS\Pro\bin\Python\Scripts
```

##### List Conda environments

```PowerShell
 Get-ChildItem "$env:LOCALAPPDATA\ESRI\conda\envs" -Directory
```

## ArcGIS Desktop (ArcMap, ArcCatalog)

ArcGIS Desktop uses Python 2.7, 32-bit version. The Background Geoprocessing extension uses it's own 64-bit Python 2.7 environment.

Refer to "[What is Python?][arcgis desktop help: what is python?]" section of the ArcMap help website.

### File System Locations

The paths provided below are for ArcGIS Desktop 10.7. If you are using a different version, the version numbers contained in the paths will differ accordingly.

| Description                                      | Path                                      |
| ------------------------------------------------ | ----------------------------------------- |
| ArcGIS Desktop Python Installation               | `%HOMEDRIVE%\Python27\ArcGIS10.7`         |
| ArcGIS 64-Bit Background Geoprocessing Extension | `%HOMEDRIVE%\Python27\ArcGISx6410.7`      |
| Per-user installed packages                      | `%APPDATA%\Python\Python27\site-packages` |
| Per-user scripts                                 | `%APPDATA%\Python\Python27\Scripts`       |

## Creating custom packages

- [Packaging Python Projects]
- [Extending geoprocessing through Python modules]

[arcgis pro python reference]: https://pro.arcgis.com/en/pro-app/arcpy/main/arcgis-pro-arcpy-reference.htm
[arcgis desktop help: what is python?]: https://desktop.arcgis.com/en/arcmap/latest/analyze/python/
[dataclasses]: https://docs.python.org/3/library/dataclasses.html
[dataclasses from pypi]: https://pypi.org/project/dataclasses/
[packaging python projects]: https://packaging.python.org/tutorials/packaging-projects/
[extending geoprocessing through python modules]: https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/extending-geoprocessing-through-python-modules.htm
[arcgis pro and conda]: https://pro.arcgis.com/en/pro-app/arcpy/get-started/what-is-conda.htm
