https://fluxcd.io/flux/installation/bootstrap/github/

```bash
curl -s https://fluxcd.io/install.sh | sudo bash
```

```bash
flux check --pre
```

```bash
export GITHUB_TOKEN=🔐β tnXTB4KiI4zxJeDEyhlLtQW1dT2bVMPcNZddE1Ne7S8MQPExFe/zyIjDgPa4h6jiO3lZ+wk+63vf5HCYEIGDrr4Z1kAC0ezu0/JAVhck8jgCfo6MI3RzIQ== 🔐
```

```bash
flux bootstrap github \
  --components-extra=image-reflector-controller,image-automation-controller \
  --owner=jhomen368 \
  --repository=home-ops \
  --branch=main \
  --path=clusters/homenet-main/apps \
  --personal \
  --token-auth
```

```bash
flux get kustomizations --watch
```

Flux Upgrade
```shell
flux bootstrap github \
  --components-extra=image-reflector-controller,image-automation-controller \
  --owner=jhomen368 \
  --repository=home-ops \
  --branch=main \
  --path=clusters/homenet-main/apps \
  --personal \
  --token-auth
```

Helm Releases
https://fluxcd.io/flux/components/helm/helmreleases/