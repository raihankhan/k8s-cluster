## Install on Linux

### Using Binary

#### For AMD64 / x86_64
```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-amd64
```
#### For ARM64
```bash
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### Using Go install
```bash
go install sigs.k8s.io/kind@v0.25.0
```

## Create A cluster

```bash
kind create cluster --image=kindest/node:v1.31.0 --name=dev --wait 5m
```

## Create A cluster with custom ha config

```bash
kind create cluster --image=kindest/node:v1.31.0 --name=dev --wait 5m --config control-plane-ha.yaml
```


## View cluster Info

```bash
kubectl cluster-info --context kind-dev
```

## Load docker image into kind cluster

```bash
kind load docker-image my-custom-image-0 my-custom-image-1
```

##  Get a list of images present on a cluster node

```bash
docker exec -it my-node-name crictl images
```





