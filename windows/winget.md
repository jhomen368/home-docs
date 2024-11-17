
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


Install