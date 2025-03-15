---
tags:
  - linux
  - patches
---

To set up automatic updates on Ubuntu using `unattended-upgrades`, follow these steps:

1. **Install the package**:
   ```bash
   sudo apt install unattended-upgrades
   ```

2. **Configure automatic updates** by editing the file `/etc/apt/apt.conf.d/50unattended-upgrades`:
   - Open the file in a text editor with root privileges:
     ```bash
     sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
     ```
   - Look for or add the following lines to enable automatic updates for security fixes and other important updates:
     ```plaintext
     Unattended-Upgrade::Allowed-Origins {
         "${distro_id}:${distro_codename}-security";
         "${distro_id}:${distro_codename}-updates";
         "${distro_id}:${distro_codename}-proposed";
         "${distro_id}:${distro_codename}-backports";
     };
     ```

   - To enable automatic updates for all available packages (not just security), add:
     ```plaintext
     Unattended-Upgrade::Automatic-Reboot "true";
     ```
     This allows the system to reboot automatically after updates if necessary.

3. **Set update frequency** by editing `/etc/apt/apt.conf.d/20auto-upgrades`:
   - Open the file:
     ```bash
     sudo nano /etc/apt/apt.conf.d/20auto-upgrades
     ```
   - Add or modify these lines to set how often updates are checked and applied (default is every 24 hours):
     ```plaintext
     APT::Periodic::Update-Package-Lists "1";
     APT::Periodic::Unattended-Upgrade "1";
     ```

4. **Enable the unattended-upgrades service**:
   ```bash
   sudo systemctl enable unattended-upgrades
   sudo systemctl start unattended-upgrades
   ```

### Example Configuration

Here’s a complete example of `/etc/apt/apt.conf.d/50unattended-upgrades`:

```plaintext
// Enable automatic updates for security fixes and other important packages
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}-security";
    "${distro_id}:${distro_codename}-updates";
};

// Allow automatic reboots after updates
Unattended-Upgrade::Automatic-Reboot "true";

// Keep a log of successful upgrades
Unattended-Upgrade::Log-Filename "/var/log/unattended-upgrades/unattended-upgrades.log";
```

### Common Pitfalls and Tips

- **Reboots**: Automatic reboots can disrupt services. Consider adding a confirmation prompt before rebooting by setting `Automatic-Reboot` to `"false"` and manually checking for updates.
  
- **Testing**: Before enabling automatic updates, test with:
  ```bash
  sudo unattended-upgrades --dry-run -v
  ```
  This simulates an update run without making changes.

- **Log Monitoring**: Regularly check `/var/log/unattended-upgrades/` to ensure updates are applied correctly and no errors occur.

By following these steps, your Ubuntu system will automatically apply security patches and other important updates, reducing the risk of vulnerabilities.
