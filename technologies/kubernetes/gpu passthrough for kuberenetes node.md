

Node:
https://docs.vmware.com/en/VMware-Edge-Compute-Stack/1.0/ecs-enterprise-edge-ref-arch/GUID-412AD9B3-6B9B-4BE0-B833-9205ACBCF956.html

https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#pre-installation-actions


```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

```
sudo apt-get update
sudo apt-get install build-essential nvidia-container-toolkit cloud-utils cloud-initramfs-growroot nfs-common -y
```

Disable Secure Boot, Add PCI Graphics

[Alt Install of NVIDIA Driver](../../knowledge/os/linux/ubuntu/installs/docker.md#Alt%20Install%20of%20NVIDIA%20Driver)

```
curl -s -o /tmp/NVIDIA-Linux-x86_64-560.35.03.run https://international.download.nvidia.com/XFree86/Linux-x86_64/560.35.03/NVIDIA-Linux-x86_64-560.35.03.run

sudo sh /tmp/NVIDIA-Linux-x86_64-560.35.03.run -s
```

https://github.com/keylase/nvidia-patch

```
curl -s -o /tmp/patch.sh https://raw.githubusercontent.com/keylase/nvidia-patch/master/patch.sh

curl -s -o /tmp/patch-fbc.sh https://raw.githubusercontent.com/keylase/nvidia-patch/master/patch-fbc.sh
```

```
sudo bash /tmp/patch.sh
sudo bash /tmp/patch-fbc.sh
```

[[#heading|displayText]]

https://github.com/NVIDIA/k8s-device-plugin

https://dischord.org/2022/05/16/k3s-rke2-and-
gpu-pci-passthrough/


```
sudo su -
mkdir -p /var/lib/rancher/rke2/agent/etc/containerd
cat > /var/lib/rancher/rke2/agent/etc/containerd/config.toml.tmpl<<'EOF'
[plugins.opt]
  path = "/var/lib/rancher/rke2/agent/containerd"

[plugins.cri]
  stream_server_address = "127.0.0.1"
  stream_server_port = "10010"
  enable_selinux = false
  sandbox_image = "index.docker.io/rancher/pause:3.6"

[plugins.cri.containerd]
  snapshotter = "overlayfs"
  disable_snapshot_annotations = true
  default_runtime_name = "nvidia"

[plugins.cri.containerd.runtimes.runc]
  runtime_type = "io.containerd.runc.v2"

[plugins.cri.containerd.runtimes."nvidia"]
  runtime_type = "io.containerd.runc.v2"
[plugins.cri.containerd.runtimes."nvidia".options]
  BinaryName = "/usr/bin/nvidia-container-runtime"
EOF
```

```
systemctl restart rke2-agent
```

https://dischord.org/2022/06/14/rke2-and-nvidia-gpus-with-the-grid-operator/
https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/getting-started.html#rancher-kubernetes-engine-2


```
helm install gpu-operator \
     -n gpu-operator --create-namespace \
     nvidia/gpu-operator \
     --set driver.enabled=false \
     --set toolkit.enabled=false \
     --set driver.licensingConfig.configMapName=licensing-config \
     --set toolkit.env[0].name=CONTAINERD_CONFIG \
     --set toolkit.env[0].value=/var/lib/rancher/rke2/agent/etc/containerd/config.toml \
     --set toolkit.env[1].name=CONTAINERD_SOCKET \
     --set toolkit.env[1].value=/run/k3s/containerd/containerd.sock \
     --set toolkit.env[2].name=CONTAINERD_RUNTIME_CLASS \
     --set toolkit.env[2].value=nvidia \
     --set toolkit.env[3].name=CONTAINERD_SET_AS_DEFAULT \
     --set-string toolkit.env[3].value=true
```

```
helm install gpu-operator -n gpu-operator --create-namespace \
  nvidia/gpu-operator $HELM_OPTIONS \
    --set toolkit.env[0].name=CONTAINERD_CONFIG \
    --set driver.enabled=false \
    --set toolkit.enabled=false \
    --set toolkit.env[0].value=/var/lib/rancher/rke2/agent/etc/containerd/config.toml.tmpl \
    --set toolkit.env[1].name=CONTAINERD_SOCKET \
    --set toolkit.env[1].value=/run/k3s/containerd/containerd.sock \
    --set toolkit.env[2].name=CONTAINERD_RUNTIME_CLASS \
    --set toolkit.env[2].value=nvidia \
    --set toolkit.env[3].name=CONTAINERD_SET_AS_DEFAULT \
    --set-string toolkit.env[3].value=true
```


https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/uninstall.html

```
Plex:
https://www.debontonline.com/2021/01/part-14-deploy-plexserver-yaml-with.html (manifests)
https://github.com/plexinc/pms-docker/tree/master/charts/plex-media-server (helm)

https://support.plex.tv/articles/201370363-move-an-install-to-another-system/

Tautulli:
https://github.com/Tautulli/Tautulli/wiki/Frequently-Asked-Questions#move-media

```


```
helm upgrade -i nvdp nvdp/nvidia-device-plugin \
  --namespace nvidia-device-plugin \
  --create-namespace \
  --version 0.15.0 \
  --values=config.yaml

```