# Beets config

## Prerequisites

Configure the `$Editor` to point to preferred text editor.
In my case, for VSCode obtained from WinGet, it is : `code.cmd --wait`

## Installation

### Windows

Prepare system with required packages.

```powershell
winget import --import-file winget-packages.json
```

or

```powershell
winget install Microsoft.VisualStudio.2022.BuildTools --force --override "--wait --passive --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 --add Microsoft.VisualStudio.Component.Windows11SDK.22000" # https://stackoverflow.com/a/55053709
winget install Rustlang.Rustup
winget install ImageMagick.ImageMagick
winget install Gyan.FFmpeg
winget install gstreamerproject.gstreamer
winget install AcoustID.Chromaprint
winget install Python.Python.3.6
```

then

```powershell
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
python -m pip install --upgrade pip
```

### Application

Set the `BEETSDIR` environment variable to correspond to this repository's path, or clone this repository in [the default location](https://docs.beets.io/en/latest/reference/config.html#id133).

```shell
pip install -r requirements.txt
```
