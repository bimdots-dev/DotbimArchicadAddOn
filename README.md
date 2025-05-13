# Archicad Dotbim Add-On

[![Build](https://github.com/bimdots-dev/DotbimArchicadAddOn/actions/workflows/build.yml/badge.svg)](https://github.com/bimdots-dev/DotbimArchicadAddOn/actions/workflows/build.yml)

Archicad Add-On to import and export [Dotbim (.bim)](https://dotbim.net) files.

## Add-On Usage

### Install

You can download the Add-On from the [Bimdots](https://bimdots.com/product/dotbim-in-out) store. Please read the [installation guide](https://bimdots.com/help-center/add-on-installation-guide) for more instructions.

### Use

You can access import from:
- `File > Open > Open...`
- `File > Interoperability > Merge... > Merge from File...`

You can access export from:
- `File > Save As...`
- `File > Interoperability > Export Dotbim File...`

## Add-On JSON interface

The Add-On registers commands to the Archicad JSON interface, so you can access export and import via an external application.

Export command example:
```json
{
    "command" : "API.ExecuteAddOnCommand",
    "parameters": {
        "addOnCommandId": {
            "commandNamespace": "Bimdots",
            "commandName": "ExportDotbimFile"
        },
        "addOnCommandParameters": {
            "filePath": "path/to/dotbim/file"
        }
    }
}
```

Import command example:
```json
{
    "command" : "API.ExecuteAddOnCommand",
    "parameters": {
        "addOnCommandId": {
            "commandNamespace": "Bimdots",
            "commandName": "ImportDotbimFile"
        },
        "addOnCommandParameters": {
            "filePath": "path/to/dotbim/file"
        }
    }
}
```

## Build instructions

### Install prerequisites

#### Windows

- [Visual Studio](https://visualstudio.microsoft.com/downloads) (any version)
  - Platform toolset v142.
  - Platform toolset v143.

#### macOS

- [Xcode](https://developer.apple.com/xcode/)
  - Version 14.2: `/Applications/Xcode_14.2.app`.
  - Version 15.2: `/Applications/Xcode_15.2.app`.

#### Common

- [CMake](https://cmake.org) (3.16+)
- [Python](https://www.python.org) (3.8+)
- [7-Zip](https://www.7-zip.org) (22+)
  - The executable must be in the PATH.

### Build

Run the build script.

```
python Tools\BuildAddOn.py --configFile config.json --acVersion 26 27 28
```
