https://fluxcd.io/flux/installation/bootstrap/github/

```bash
curl -s https://fluxcd.io/install.sh | sudo bash
```

```bash
flux check --pre
```

```bash
export GITHUB_TOKEN=🔐β s4Fsg5P8m8wnIXLxpRWYDH9GmZW87PLGfuIcYBOzGN7qQ5+xZvu39vexNE2MRnRgIfma/8nvPeWO2dyqqK+a7T/VeS+vH5TKNDN4pqxj/MTDmrafDMftCgeaA8/n7XSGbTU4vg2ypb6Oa6OkMiVvfH/RLxla+bxby3ysgadRfwCJkhRBnwHbuXQjfNHs 🔐
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