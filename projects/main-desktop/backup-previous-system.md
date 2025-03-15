---
tags:
  - windows
---

## Windows Subsystem for Linux (WSL)

### Exporting a Distribution

To back up your WSL distribution, you can use the `wsl --export` command. This is particularly useful when you want to save your current setup before making significant changes or moving it to another machine.

1. **List Installed Distributions**:  
   First, check which distributions are installed and their statuses by running:
   ```powershell
   wsl -l -v
   ```
   This command lists all installed Linux distributions along with their version (e.g., 2) and current status (e.g., Running or Stopped).

2. **Export the Distribution**:  
   Once you've identified the distribution you want to back up, use the following command:
   ```powershell
   wsl --export Ubuntu-22.04 "C:\Users\Josh\OneDrive\Documents\backups\2025 PC\Ubuntu-22.04.tar"
   ```
   Replace `Ubuntu-22.04` with the name of your distribution and adjust the path to where you want to save the backup file. The `.tar` file will contain all your files, settings, and packages.

### Importing a Distribution

If you need to restore or move a WSL distribution to another machine, use the `wsl --import` command.

1. **Create a Directory for the Distribution**:  
   Before importing, create a directory where the distribution will be stored:
   ```powershell
   mkdir "C:\Users\Josh\OneDrive\Documents\wsl"
   ```

2. **Import the Distribution**:  
   Run the following command to import the `.tar` file:
   ```powershell
   wsl --import Ubuntu-22.04 "C:\Users\Josh\OneDrive\Documents\wsl" "C:\Users\Josh\OneDrive\Documents\backups\2025 PC\Ubuntu-22.04.tar"
   ```
   This will create a new distribution named `Ubuntu-22.04` in the specified directory.

3. **Start the Distribution**:  
   After importing, you can start the distribution by typing its name in PowerShell or the Start menu.

---

## Steam Wallpaper Engine

The Steam Wallpaper Engine allows you to create and share dynamic wallpapers directly from Steam. If you want to back up your custom wallpapers or themes, follow these steps:

1. **Backup Your Wallpapers**:  
   Visit the [official backup guide](https://help.wallpaperengine.io/en/steam/backup.html) for detailed instructions on exporting your settings and themes.

2. **Restore Your Wallpapers**:  
   If you need to restore your wallpapers on a new machine, import the backed-up files using the same guide.

Backing up your work ensures that you don't lose any customizations or progress, especially if you plan to reinstall Steam or switch devices.

---

## Peace Equalizer

Peace is an open-source audio equalization tool designed for high-quality sound processing. It's particularly popular among audiophiles and gamers who want to fine-tune their audio experience.

1. **Download Peace**:  
   You can download the latest version of Peace from [SourceForge](https://sourceforge.net/projects/peace-equalizer-apo-extension/files/latest/download).

2. **Installation and Setup**:  
   Once installed, Peace integrates with your system's audio processing pipeline, allowing you to adjust frequencies and create custom sound profiles.

3. **Customization**:  
   Use Peace to enhance bass, treble, or any other frequency range according to your preferences. It supports both real-time adjustments and preset configurations.

4. **Compatibility**:  
   Peace works with a variety of audio interfaces and is compatible with most modern Windows systems.

If you encounter issues or need support, check the official forums or documentation for troubleshooting tips and updates.

