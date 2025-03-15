
## Debloat
https://github.com/Raphire/Win11Debloat

``` powershell
& ([scriptblock]::Create((irm "https://win11debloat.raphi.re/"))) -RunDefaults -Silent
```

### User Customizations

https://github.com/farag2/Sophia-Script-for-Windows
https://github.com/farag2/Sophia-Script-for-Windows/releases/tag/6.7.2
https://github.com/farag2/Sophia-Script-for-Windows/releases/download/6.7.2/Sophia.Script.Wrapper.v2.7.4.zip

![Sophia Script for Windows 11 Customized](../../artifacts/win11-debloat/Sophia_Script_for_Windows_11_v6.7.2_customized.zip)

``` powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass
cmd /C curl -O -L -H "Accept: Accept: application/vnd.github.v3.raw" -H "Authorization: Bearer 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" https://api.github.com/repos/jhomen368/home-docs/contents/windows/files/Sophia_Script_for_Windows_11_v6.7.3_customized.zip

Expand-Archive Sophia_Script_for_Windows_11_v6.7.3_customized.zip

Start-Process PowerShell -Verb runAs -ArgumentList "./Sophia_Script_for_Windows_11_v6.7.3_customized/Sophia.ps1"
```

### Install NVIDIA App
Temp until winget PR closed (https://github.com/microsoft/winget-pkgs/issues/140696)

https://gist.github.com/emilwojcik93/788eca2e456488c360fabc15d274031d?permalink_comment_id=5294025#gistcomment-5294025

Use `Invoke-RestMethod` to download and execute the script. Here is how you can do it:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force; irm 
https://gist.githubusercontent.com/emilwojcik93/788eca2e456488c360fabc15d274031d/raw/Install-NvidiaApp.ps1 | iex
```

## Application Installs

## Install personalized basic package list from git

![basic_apps.json](../../artifacts/winget/basic_apps.json)

``` powershell
cmd /C curl -O -L -H "Accept: Accept: application/vnd.github.v3.raw" -H "Authorization: Bearer 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" https://api.github.com/repos/jhomen368/home-docs/contents/windows/files/basic_apps.json

winget import -i .\basic_apps.json --no-upgrade --accept-package-agreements --accept-source-agreements

rm basic_apps.json
```


![custom_apps.json](../../artifacts/winget/custom_apps.json)

``` powershell
cmd /C curl -O -L -H "Accept: Accept: application/vnd.github.v3.raw" -H "Authorization: Bearer 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" https://api.github.com/repos/jhomen368/home-docs/contents/windows/files/custom_apps.json

winget import -i .\custom_apps.json --no-upgrade --accept-package-agreements --accept-source-agreements

rm custom_apps.json
```
