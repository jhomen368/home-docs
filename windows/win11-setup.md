
## Debloat
https://github.com/Raphire/Win11Debloat

``` powershell
& ([scriptblock]::Create((irm "https://win11debloat.raphi.re/"))) -RunDefaults -Silent
```

## User Customizations

https://github.com/farag2/Sophia-Script-for-Windows
https://github.com/farag2/Sophia-Script-for-Windows/releases/tag/6.7.2
https://github.com/farag2/Sophia-Script-for-Windows/releases/download/6.7.2/Sophia.Script.Wrapper.v2.7.4.zip

![Sophia Script for Windows 11 Customized](files/Sophia_Script_for_Windows_11_v6.7.2_customized.zip)

``` powershell
cmd /C curl -O -L -H "Accept: Accept: application/vnd.github.v3.raw" -H "Authorization: Bearer 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" https://api.github.com/repos/jhomen368/home-docs/contents/windows/files/Sophia_Script_for_Windows_11_v6.7.2_customized.zip

Expand-Archive Sophia_Script_for_Windows_11_v6.7.2_customized.zip

Start-Process PowerShell -Verb runAs -ArgumentList "./Sophia_Script_for_Windows_11_v6.7.2_customized/Sophia.ps1"
```
