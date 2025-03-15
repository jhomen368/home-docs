
## Ubuntu

https://linuxopsys.com/ubuntu-automatic-updates

```
sudo apt install unattended-upgrades
```

Modify file at /etc/apt/apt.conf.d/50unattended-upgrades


Setup ubuntu to use unattended-upgrades

To set up automatic security updates on your Ubuntu system using `unattended-upgrades`, follow these organized steps:

1. **Install the Package**:
   Open your terminal and run the command to install `unattended-upgrades`:
   ```bash
   sudo apt install unattended-upgrades
   ```

2. **Configure the Settings**:
   Edit the configuration file using nano:
   ```bash
   sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
   ```
   - **Allowed Origins**: Add your Ubuntu version (e.g., 'Focal' for 20.04) to ensure updates are applied correctly.
     Example entry:
     ```plaintext
     "o=Ubuntu,a=Focal";
     ```
   - **Auto-Fix Options**: Change `Download` to `Apply` or `Apply-Network` to automatically install updates and reboot if necessary.
     Example setting:
     ```plaintext
     AutoFix::Apply;
     ```
   - **Email Notifications**: Update the email address to receive notifications about issues.
     Example configuration:
     ```plaintext
     "you@example.com";
     ```

3. **Enable and Start the Service**:
   Enable and start the `unattended-upgrades` service with:
   ```bash
   sudo systemctl enable --now unattended-upgrades
   ```
   Verify the service status using:
   ```bash
   systemctl status unattended-upgrades
   ```

4. **Considerations**:
   - **Update Types**: This setup primarily handles security updates. Other package updates may require additional tools.
   - **Frequency**: Updates run daily by default via cron. Adjusting this schedule might be needed based on your preferences.

By following these steps, your system will automatically handle security updates, enhancing stability and security with minimal manual intervention.
