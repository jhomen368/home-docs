Install personalized basic package list from git

![[basic_apps.json]]

``` cmd
curl -O -L -H "Accept: Accept: application/vnd.github.v3.raw" -H "Authorization: Bearer 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" https://api.github.com/repos/jhomen368/home-docs/contents/windows/files/basic_apps.json

winget import -i .\basic_apps.json
```

Search for App

``` powershell
winget search Discord
```

Install an app

``` powershell
winget install Discord.Discord
```

Upgrade all apps

``` powershell
winget upgrade --all
```


Upgrade specific app

``` powershell
winget upgrade Discord.Discord
```


Export all winget apps into JSON into current working directory

``` powershell
winget export -o exported_apps.json
```

Install winget apps from JSON in current working directory

``` powershell
winget import -i exported_apps.json
```

