---
title: ArcGIS and Python
layout: page
permalink: /python/legacy/arcgis/
---

It is recommended to use ArcGIS Pro for new development unless there is a specific need to use Desktop for a feature that is not available in Pro. Desktop uses Python 2.7, which is **no longer supported as of January 2020**.

## ArcGIS Pro

Please familiarize yourself with the [ArcGIS Pro Python Reference] section of the ArcGIS Pro documentation.

### Known issues with Conda

[It is not uncommon to encounter issues when [Conda] is started from the command prompt](<https://github.com/conda/conda/issues/11308>). Below are some tips to help work around these issues.

* Use Windows Command prompt (`cmd.exe`) rather than PowerShell (`pwsh.exe` or the older `powershell.exe`) when using Conda.
* When you open a terminal in Visual Studio Code, it may automatically run `conda activate`, which will fail with various error messages. You can use the `activate.bat` batch file in its place. (This batch file can be found in the locations described in the "Conda and batch files" section of the [File Locations](#file-locations) table below.)

#### `activate` vs `conda activate`

Below you will see the response from `activate` followed by `conda activate`.

##### activate

```cmd
C:\Users\your-user-name\Documents\GitHub\your-repo>activate arcgispro-py3

(arcgispro-py3) C:\Users\your-user-name\Documents\GitHub\your-repo>
```

##### conda activate

Below is what you will probably see if you try to use `conda activate`: you'll get an error message and your environment won't actually be activated. The error message will offer suggestions that don't actually work.

<!-- cspell: disable -->
```cmd
C:\Users\your-user-name\Documents\GitHub\your-repo>conda activate arcgispro-py3

CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.

If using 'conda activate' from a batch script, change your
invocation to 'CALL conda.bat activate'.

To initialize your shell, run

    conda init <SHELL_NAME>

Currently supported shells are:

* bash
* cmd.exe
* fish
* tcsh
* xonsh
* zsh
* powershell

See 'conda init --help' for more information and options.

IMPORTANT: You may need to close and restart your shell after running 'conda init'.
```
<!-- cspell: enable -->

### [Conda] Environments

ArcGIS Pro uses [Conda] to manage multiple environments, as documented in [ArcGIS Pro and Conda].

### File locations

This section describes where various files related to ArcGIS Pro's Python installation can be found. The text surrounded by percent signs (`%`) are environment variables.

| Description                                  | Location                                                          |
| -------------------------------------------- | ----------------------------------------------------------------- |
| Default Conda environment (Python EXE, etc.) | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\envs\arcgispro-py3`         |
| Conda and batch files                        | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\Scripts`                    |
| All users' scripts folder                    | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\Scripts` |
| Per-user scripts folder (installed via pip)  | `%APPDATA%\Python\Python`_37_`\Scripts`[^1]                         |
| Custom Conda environments                    | `%LOCALAPPDATA%\ESRI\conda\envs\`_your-env-name_                  |
| Scripts installed via Conda                  | `%LOCALAPPDATA%\ESRI\conda\envs\`_your-env-name_`\Scripts`        |

[^1]: The number after the word Python may differ depending on the version of ArcGIS Pro installed. ArcGIS Pro 2.9 comes with Python 3.7, so the folder name is `Python36`.

#### Useful commands

All commands are for PowerShell unless otherwise noted.

##### Add a folder to the system path

```pwsh
$env:Path += ";$env:PROGRAMFILES\ArcGIS\Pro\bin\Python\Scripts"
```

Windows Batch File equivalent

```batch
SET PATH=%PATH%;%PROGRAMFILES%\ArcGIS\Pro\bin\Python\Scripts
```

##### List [Conda] environments

Using [Conda CLI commands] (should work cmd.exe or elsewhere):

```cmd
conda env list
```

Using Powershell to find environments by examining the directory where Conda environments are stored.

```pwsh
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

* [Packaging Python Projects]
* [Extending geoprocessing through Python modules]

[arcgis pro and conda]: https://pro.arcgis.com/en/pro-app/arcpy/get-started/what-is-conda.htm
[arcgis pro python reference]: https://pro.arcgis.com/en/pro-app/arcpy/main/arcgis-pro-arcpy-reference.htm
[arcgis desktop help: what is python?]: https://desktop.arcgis.com/en/arcmap/latest/analyze/python/
[conda]:https://conda.io/projects/conda/en/latest/
[Conda CLI commands]:https://conda.io/projects/conda/en/latest/commands.html
[packaging python projects]: https://packaging.python.org/tutorials/packaging-projects/
[extending geoprocessing through python modules]: https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/extending-geoprocessing-through-python-modules.htm
