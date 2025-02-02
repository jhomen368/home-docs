
## Ubuntu 

Configure automatic updates for ubuntu server using unattended-upgrades via command line

### Configuring Automatic Updates for Ubuntu Server Using Unattended-Upgrades via Command Line

To configure automatic updates for an Ubuntu server using the `unattended-upgrades` package, follow these steps:

**Step 1: Install the `unattended-upgrades` Package**

Open a terminal on your Ubuntu server and run the following command:
```bash
sudo apt-get install unattended-upgrades
```
This will install the `unattended-upgrades` package, which is responsible for automatically upgrading packages.

**Step 2: Configure the `unattended-upgrades` Configuration File**

The `unattended-upgrades` configuration file is located at `/etc/apt/apt.conf.d/50unattended-upgrades`. To configure the file, run the following command:
```bash
sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
```
This will open the file in the `nano` editor. Add the following lines to the end of the file:
```makefile
// Automatically upgrade packages
Unattended-Upgrade::Allowed-Origins::Regex {
    "^https://security.ubuntu.com.*$";
};

// Upgrade all packages, except for those that are explicitly excluded
Unattended-Upgrade::Package-Blacklist {
    "mysql-server";
};
```
The first line specifies the allowed origins for automatic upgrades, which in this case is only security updates from Ubuntu's official repositories.

The second line specifies a blacklist of packages that should not be upgraded automatically. In this example, we're excluding the `mysql-server` package to prevent it from being upgraded unnecessarily.

**Step 3: Enable Automatic Upgrades**

To enable automatic upgrades, run the following command:
```bash
sudo dpkg-reconfigure -plow unattended-upgrades
```
This will prompt you to configure the `unattended-upgrades` package. Follow the prompts to enable automatic upgrades and set the upgrade interval to your desired frequency (e.g., daily).

**Step 4: Verify Automatic Upgrades**

To verify that automatic upgrades are working, run the following command:
```bash
sudo unattended-upgrade -v
```
This will display information about the last automatic upgrade attempt, including any packages that were upgraded or skipped.

That's it! With these steps, you've successfully configured automatic updates for your Ubuntu server using `unattended-upgrades`.
