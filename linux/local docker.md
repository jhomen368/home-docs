Run a container to work in

```
docker run -it --rm -v ${HOME}:/root/ -v ${PWD}:/work -w /work --net host {IMAGE} sh
```

 - `alpine/ansible`
