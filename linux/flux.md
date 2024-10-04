https://fluxcd.io/flux/installation/bootstrap/github/

```
curl -s https://fluxcd.io/install.sh | sudo bash
```

```
flux check --pre
```

```
export GITHUB_TOKEN=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
```

```
flux bootstrap github \
  --components-extra=image-reflector-controller,image-automation-controller \
  --owner=jhomen368 \
  --repository=home-ops \
  --branch=main \
  --path=clusters/homenet-main/apps \
  --personal \
  --token-auth
```

```
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