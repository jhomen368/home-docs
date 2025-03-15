
Winget is a powerful package manager built into Windows 10 and later versions, designed to simplify the process of searching for, installing, upgrading, and managing applications. Below are some essential commands and examples that demonstrate how to use Winget effectively.  

---

## **Search for an Application**  
To search for an application in the Winget repository, use the following command:  

```powershell
winget search <app-name>
```  

For example, if you want to search for Discord, run:  

```powershell
winget search Discord
```  

This will display a list of applications related to your search query. The output typically includes details such as the app name, ID (used for installation), version, and publisher.  

## **Install an Application**  
Once you have identified the application you want to install, use its unique identifier (ID) to install it. The general syntax is:  

```powershell
winget install <app-id>
```  

For example, to install Discord, run:  

```powershell
winget install Discord.Discord
```  

Here, `Discord.Discord` is the app ID, where the first part (`Discord`) represents the publisher, and the second part (`Discord`) is the application name. Winget will download and install the latest version of the application automatically.  

## **Upgrade All Applications**  
To ensure all your installed applications are up to date, use the following command:  

```powershell
winget upgrade --all
```  

This command checks for updates for all installed applications and applies them if available. It is a convenient way to keep your software ecosystem current without manually checking each app.  

## **Upgrade a Specific Application**  
If you want to update only a specific application, use its ID with the `upgrade` command:  

```powershell
winget upgrade <app-id>
```  

For example, to upgrade Discord, run:  

```powershell
winget upgrade Discord.Discord
```  

This ensures that only the specified application is checked for updates and upgraded if necessary.  

## **Export All Installed Applications to JSON**  
Winget allows you to export a list of all installed applications into a JSON file. This can be useful for backup purposes or transferring your app installations to another device. Use the following command:  

```powershell
winget export -o exported_apps.json
```  

This will create a `exported_apps.json` file in your current working directory, containing details about all installed applications, including their IDs and versions.  

## **Import Applications from JSON**  
If you have an exported JSON file of applications, you can use it to reinstall the same set of applications on another device or after a clean install. Use the following command:  

```powershell
winget import -i exported_apps.json
```  

This will read the JSON file and install all listed applications automatically, including their dependencies. 