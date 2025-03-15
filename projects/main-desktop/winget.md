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

