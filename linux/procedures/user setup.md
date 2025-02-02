
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
