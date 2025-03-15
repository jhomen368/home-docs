
## Ansible Installation Steps

### Check Python Version
Run the command `python3 -m pip --version` to check your Python version.
### Install Pip
Use the following command to download and install pip:
```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py --user
```
### Install Ansible Core
Install Ansible core using pip:
```bash
python3 -m pip install --user ansible-core
```

### Install Ansible Development Tools
Next, install the Ansible development tools:
```bash
python3 -m pip install --user ansible-dev-tools
```

### Add Local Bin to Path
Add the local bin directory to your system's PATH environment variable by running:
```bash
echo 'export PATH="~/local/bin:$PATH"' >> ~/.bashrc
```

### Reload Bash Configuration
Finally, reload your bash configuration file using:
```bash
source ~/.bashrc
```
This will update your shell with the new PATH environment variable.

To install Ansible on your system, follow these organized and verified steps:

### Step 1: Check Python Version
Run the command to check your Python version:
```bash
python3 --version
```

### Step 2: Install pip
Download and install pip using the following commands. If curl is not installed, you might need to install it first.
```bash
sudo apt-get install curl  # For Debian/Ubuntu systems
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py --user
```

### Step 3: Install Ansible Core
Install Ansible core using pip:
```bash
python3 -m pip install --user ansible-core
```

### Step 4: Install Ansible Development Tools
Install additional development tools:
```bash
python3 -m pip install --user ansible-dev-tools
```

### Step 5: Update PATH Environment Variable
Add the local bin directory to your PATH. Use `$HOME` for reliability:
```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
```

### Step 6: Reload Bash Configuration
Apply the changes by reloading your bash configuration:
```bash
source ~/.bashrc
```

### Verification
After installation, verify Ansible is correctly installed by checking its version:
```bash
ansible --version
```

This should display the installed version of Ansible, confirming a successful setup.
