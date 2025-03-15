---
tags:
  - windows
  - win11
---
## Debloating Windows 11

The process of removing unnecessary default apps and services from Windows 11 is known as "debloating." This can improve system performance and reduce resource usage.

### Using Win11Debloat

[Win11Debloat](https://github.com/Raphire/Win11Debloat) is a popular PowerShell script designed to remove bloatware from Windows 11. It offers various options for customization, including removing specific apps or services.

#### Running the Script

```powershell
# Execute Win11Debloat with default settings and suppress output
& ([scriptblock]::Create((irm "https://win11debloat.raphi.re/"))) -RunDefaults -Silent
```

**Flags Explanation:**
- `-RunDefaults`: Applies the most common debloating actions.
- `-Silent`: Runs the script without user interaction or output.

## User Customizations

Sophia Script for Windows 11 is a powerful tool for customizing your system. It allows you to tweak various settings, disable telemetry, and optimize performance.

### Sophia Script Installation

#### Downloading the Script

```powershell
# Set execution policy to allow script execution
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force

# Download the customized version of Sophia Script
curl -O https://github.com/jhomen368/home-docs/blob/main/artifacts/win11-debloat/Sophia_Script_for_Windows_11_v6.7.3_customized.zip
```

#### Installing the Script

```powershell
# Extract the downloaded archive
Expand-Archive Sophia_Script_for_Windows_11_v6.7.3_customized.zip

# Run the script with administrative privileges
Start-Process PowerShell -Verb runAs -ArgumentList "./Sophia_Script_for_Windows_11_v6.7.3_customized/Sophia.ps1"
```

**Note:** Ensure you review the script's contents before execution to understand the changes it will make.

## Installing NVIDIA App

Until the official winget package is available, you can use a PowerShell script to install the NVIDIA App.

### Installation Script

```powershell
# Set execution policy and download/install the NVIDIA App
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force; irm https://gist.githubusercontent.com/emilwojcik93/788eca2e456488c360fabc15d274031d/raw/Install-NvidiaApp.ps1 | iex
```

**Note:** This is a temporary workaround. Monitor the [winget issue](https://github.com/microsoft/winget-pkgs/issues/140696) for updates.

## Application Installation

### Installing from Custom Package List

This section outlines how to install applications using a custom winget package list.

#### Importing Packages

```powershell
# Download the custom apps configuration file
curl -O https://github.com/jhomen368/home-docs/blob/main/artifacts/winget/custom_apps.json

# Import and install packages from the JSON file
winget import -i .\custom_apps.json --no-upgrade --accept-package-agreements --accept-source-agreements

# Clean up by removing the configuration file
rm custom_apps.json
```

**Flags Explanation:**
- `--no-upgrade`: Prevents existing packages from being upgraded.
- `--accept-package-agreements` and `--accept-source-agreements`: Automatically accepts all terms of use.

## Best Practices

1. **Backup Your System:** Always create a backup before making significant changes to your system.
2. **Verify Sources:** Ensure scripts and tools are downloaded from trusted sources.
3. **Test Changes:** Apply changes in a controlled environment before implementing them widely.
4. **Monitor Performance:** After customization, monitor system performance to identify any issues.

By following this guide, you can effectively debloat your Windows 11 system, apply customizations, and install essential applications.
