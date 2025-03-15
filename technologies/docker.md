---
tags:
  - linux
  - docker
---

# Install Docker on Ubuntu

Docker is a powerful platform for containerization, allowing you to package and ship applications in isolated environments. This guide will walk you through the process of installing Docker on an Ubuntu system.

## Prerequisites
Before starting, ensure your system meets these requirements:
- **Ubuntu 20.04 or later** (other Linux distributions may require different steps)
- **Root or sudo access**
- An active internet connection
## Step 1: Update System Packages
First, update your existing packages to ensure compatibility:

```bash
sudo apt-get update
```

## Step 2: Install Required Dependencies
Install necessary tools and certificates:

```bash
sudo apt-get install ca-certificates curl
```

These packages provide essential security certificates and the `curl` utility for downloading files.

## Step 3: Add Docker’s GPG Key
Docker uses GPG keys to verify software authenticity. Add the official key with these commands:

1. Create a directory for storing the key:
   ```bash
   sudo install -m 0755 -d /etc/apt/keyrings
   ```

2. Download and store the Docker GPG key:
   ```bash
   sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   ```

3. Ensure the key has proper permissions:
   ```bash
   sudo chmod a+r /etc/apt/keyrings/docker.asc
   ```

## Step 4: Add Docker Repository to Sources
To install Docker, add its repository to your system's package sources:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

This command adds the repository with:
- **Architecture**: Automatically detected based on your system.
- **Signing key**: Points to the GPG key added earlier.
- **Ubuntu version**: Uses your current OS release codename (e.g., `focal` for 20.04).
- **Channel**: Installs from the `stable` channel.

## Step 5: Update Package Index
After adding the repository, update your package index:

```bash
sudo apt-get update
```

## Step 6: Install Docker Packages
Install the latest stable versions of Docker components:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Here’s what each package does:
- **docker-ce**: The Docker Engine (community edition).
- **docker-ce-cli**: Command-line interface for Docker.
- **containerd.io**: Container runtime.
- **docker-buildx-plugin**: Plugin for building multi-platform images.
- **docker-compose-plugin**: Plugin for defining and running multi-container setups.

## Step 7: Add User to Docker Group
To run Docker commands without `sudo`, add your user to the `docker` group:

```bash
sudo usermod -aG docker $USER
```

After running this command, log out and back in for the changes to take effect. You can test it by running:

```bash
docker run hello-world
```

If successful, you’ll see a message confirming Docker is working correctly.

## Step 8: Verify Installation
Check if Docker is installed properly by viewing its version:

```bash
docker --version
```

Expected output:
```
Docker version 24.0.x, build abcdef123
```

## Troubleshooting Common Issues

### Issue: "Permission denied" when running Docker commands
**Solution:** Ensure you’ve added your user to the `docker` group and logged out/in.

### Issue: "Package not found"
**Solution:** Verify that your Ubuntu version is supported by Docker. Check the official [Docker documentation](https://docs.docker.com/engine/install/ubuntu/) for compatibility.

# Configure Docker to Use NVIDIA Card on Ubuntu

This guide will walk you through the steps to configure Docker to utilize an NVIDIA graphics card on Ubuntu 24.04 LTS. The process involves cleaning up old NVIDIA drivers, installing the correct drivers, and setting up Docker with NVIDIA support.

## Clean Up Old NVIDIA Drivers

Before installing new drivers, it's essential to remove any existing NVIDIA drivers to avoid conflicts.

```bash
sudo apt-get purge nvidia*
sudo apt-get autoremove
```

**Explanation:**  
- `sudo apt-get purge nvidia*`: This command removes all packages related to NVIDIA.
- `sudo apt-get autoremove`: Removes unnecessary dependencies that were installed with the NVIDIA packages.

## Install NVIDIA Driver

### Step 1: Install Required Headers

```bash
sudo apt install linux-headers-$(uname -r)
```

**Explanation:**  
The headers are necessary for compiling the NVIDIA kernel module.

### Step 2: Add CUDA Repository and Update

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt update
```

**Explanation:**  
- `wget ...`: Downloads the CUDA keyring package.
- `sudo dpkg -i ...`: Installs the keyring, which is used to verify the authenticity of NVIDIA packages.
- `sudo apt update`: Updates the package list with the new repository.

### Step 3: Install NVIDIA Drivers

```bash
sudo apt install nvidia-open
```

**Explanation:**  
Installs the open-source NVIDIA driver. This is suitable for most users who don't need proprietary features.

For access to CUDA and other proprietary features, use:

```bash
sudo apt install cuda-drivers
```

## Alternative Installation Method

If you prefer to manually download the driver or need a specific version, follow these steps.

### Automated Download

```bash
curl -s https://download.nvidia.com/XFree86/Linux-x86_64/latest.txt | awk '{print $2}' | xargs -I{} curl -o /tmp/NVIDIA.run https://download.nvidia.com/XFree86/Linux-x86_64/{}
```

**Explanation:**  
- `curl -s ...`: Silently fetches the latest driver version.
- `awk '{print $2}'`: Extracts the version number.
- `xargs -I{} ...`: Downloads the driver with the extracted version.

### Manual Download

```bash
curl -o /tmp/NVIDIA.run https://download.nvidia.com/XFree86/Linux-x86_64/570.124.04/NVIDIA-Linux-x86_64-570.124.04.run
```

**Explanation:**  
Replace `570.124.04` with the desired version number.

### Install Driver

```bash
sudo sh /tmp/NVIDIA.run -s
```

**Explanation:**  
Runs the installer script in silent mode, which automatically accepts the license agreement and installs the driver.

## Configure Docker to Use NVIDIA Card

To enable Docker containers to utilize the NVIDIA GPU, install the NVIDIA Container Toolkit.

### Step 1: Add Repository

```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

**Explanation:**  
- `curl -fsSL ...`: Fetches the GPG key and saves it.
- `sudo gpg --dearmor ...`: Converts the GPG key to a binary format.
- The subsequent commands add the NVIDIA Container Toolkit repository with proper signing.

### Step 2: InstallToolkit

```bash
sudo apt-get update
sudo apt-get install -y nvidia-container-toolkit
```

**Explanation:**  
Updates the package list and installs the toolkit, which provides runtime libraries for GPU containers.

### Step 3: Configure Docker

```bash
sudo nvidia-ctk runtime configure --runtime=docker
```

**Explanation:**  
Configures Docker to use the NVIDIA runtime, enabling GPU support in containers.

### Step 4: Restart Docker

```bash
sudo systemctl restart docker
```

**Explanation:**  
Restarts Docker to apply the changes.

## Verify Installation

To ensure everything works correctly, run a test container:

```bash
docker run --rm --gpus all nvidia/cuda:12.0-base-ubuntu22.04
```

**Explanation:**  
- `--gpus all`: Grants access to all GPUs.
- `nvidia/cuda:12.0-base-ubuntu22.04`: A CUDA-enabled container image.

If the container starts without errors, your setup is successful.

# Misc Commands

Run a container interactively with volumes and network settings:

```bash
docker run -it --rm -v ${HOME}:/root/ -v ${PWD}:/work -w /work --net host {IMAGE} sh
```

- Example: `docker run -it --rm -v ${HOME}:/root/ -v $(pwd):/work -w /work --net host alpine/ansible sh`

List running containers:

```bash
docker ps
```

Show all containers (including stopped):

```bash
docker ps -a
```

Stop a container:

```bash
docker stop [container_id]
```

Remove a container:

```bash
docker rm [container_id]
```

Force remove a running container:

```bash
docker rm -f [container_id]
```

Inspect container details:

```bash
docker inspect [container_id]
```

List Docker images:

```bash
docker images
```

Remove an image:

```bash
docker rmi [image_id]
```

Clean up unused resources:

```bash
docker system prune
```

List Docker volumes:

```bash
docker volume ls
```

Remove a volume:

```bash
docker volume rm [volume_name]
```

Check container ports:

```bash
docker port [container_id]
```

View container logs:

```bash
docker logs [container_id]
```
