---
title: ArcGIS and Python
layout: page
permalink: /python/arcgis/
---

Please familiarize yourself with the [ArcGIS Pro Python Reference] section of the ArcGIS Pro documentation.

⚠ This page is for ArcGIS Pro 3.1 or newer. For older versions, see the [legacy](legacy/ArcGIS%20and%20Python.md) page.

### [Conda] Environments

ArcGIS Pro uses [Conda] to manage multiple environments, as documented in [ArcGIS Pro and Conda].

### File locations

<details>

<summary>
This section describes where various files related to ArcGIS Pro's Python installation can be found.
</summary>

The text surrounded by percent signs (`%`) are environment variables.

| Description                                  | Location                                                          |
| -------------------------------------------- | ----------------------------------------------------------------- |
| Default Conda environment (Python EXE, etc.) | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\envs\arcgispro-py3`         |
| Conda and batch files                        | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\Scripts`                    |
| All users' scripts folder                    | `%PROGRAMFILES%\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\Scripts` |
| Per-user scripts folder (installed via pip)  | `%APPDATA%\Python\Python`_39_`\Scripts`[^1]                         |
| Custom Conda environments                    | `%LOCALAPPDATA%\ESRI\conda\envs\`_your-env-name_                  |
| Scripts installed via Conda                  | `%LOCALAPPDATA%\ESRI\conda\envs\`_your-env-name_`\Scripts`        |

[^1]: The number after the word Python may differ depending on the version of ArcGIS Pro installed. ArcGIS Pro 3.1 comes with Python 3.9.16, so the folder name is `Python39`.

</details>

#### List [Conda] environments

Using [Conda CLI commands] (should work cmd.exe or elsewhere):

```cmd
conda env list
```

Using Powershell to find environments by examining the directory where Conda environments are stored.

```pwsh
 Get-ChildItem "$env:LOCALAPPDATA\ESRI\conda\envs" -Directory
```

## Creating custom packages

* [Packaging Python Projects]
* [Extending geoprocessing through Python modules]

[arcgis pro and conda]: https://pro.arcgis.com/en/pro-app/arcpy/get-started/what-is-conda.htm
[arcgis pro python reference]: https://pro.arcgis.com/en/pro-app/arcpy/main/arcgis-pro-arcpy-reference.htm
[conda]:https://conda.io/projects/conda/en/latest/
[Conda CLI commands]:https://conda.io/projects/conda/en/latest/commands.html
[packaging python projects]: https://packaging.python.org/tutorials/packaging-projects/
[extending geoprocessing through python modules]: https://pro.arcgis.com/en/pro-app/arcpy/geoprocessing_and_python/extending-geoprocessing-through-python-modules.htm

## Powershell profile setup

Put this into your [Powershell profile script][pwsh profiles] to have Powershell only start Conda when starting in a folder containing Python files containing the text `arcpy`.

It will also add a function called `Initialize-Conda` which will let you do this manually.

```powershell
# Examples for pre-Conda setup.

# Setup posh-git
Import-Module posh-git

# If you use oh-my-posh, set it up before setting up Conda if you want
# the prompt to display your current conda environment.
oh-my-posh init pwsh | Invoke-Expression

# --> Conda stuff starts here <--

# Detect if conda should be loaded.
New-Variable -Name hasArcPy -Value (
    # Get the first pythons with the text "arcpy" in it.
    (Get-ChildItem **\*.py,**\*.pyt -Recurse | Select-String 'arcpy' -List
    # Select only the first item. We just need to see if any are there,
    # so we don't need more than one.
    | Select-Object -First 1
    # Return true if matches were found, false otherwise.
    ).Length -ge 1
) -Scope Private

<#
.SYNOPSIS
    You can use this function to initialize conda if it is not auto-detected.
#>
function Initialize-Conda {
    Write-Progress "Initializing Conda"
    # To see what the command below is doing, run that line without the trailing `| Invoke-Expression`.
    (& "C:\Program Files\ArcGIS\Pro\bin\Python\Scripts\conda.exe" "shell.powershell" "hook") | Out-String | Invoke-Expression
}

# Initialize Conda only if an arcpy script is detected.
if ($hasArcPy) {
    Initialize-Conda
} else {
    Write-Host "Conda was not initialized automatically. If you would like to do so, use the Initialize-Conda command."
}

Remove-Variable hasArcPy
```

[pwsh profiles]:https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles