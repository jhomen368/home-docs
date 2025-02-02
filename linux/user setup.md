## Ansible Install
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#pipx-install

``` bash
python3 -m pip -V
```

```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py --user
```

```bash
python3 -m pip install --user ansible-core
```

```bash
python3 -m pip install ansible-dev-tools --user
```

Add ./local/bin to path

```bash
echo 'export PATH="./local/bin:$PATH"' >> ~/.bashrc
```

reload bashrc

``` bash
source ~/.bashrc
```
