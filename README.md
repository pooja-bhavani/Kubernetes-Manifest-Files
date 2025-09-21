# Used Amazon Q with MCP Servers to generate manifest files
![image](https://github.com/user-attachments/assets/e8699222-6445-4231-85cb-fb6eb969d89e)

# KIND Cluster Setup 
1. Installing KIND and kubectl 
```

#!/bin/bash 

[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.27.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

VERSION="v1.30.0"
URL="https://dl.k8s.io/release/${VERSION}/bin/linux/amd64/kubectl"
INSTALL_DIR="/usr/local/bin"

curl -LO "$URL"
chmod +x kubectl
sudo mv kubectl $INSTALL_DIR/
kubectl version --client

rm -f kubectl
rm -rf kind

```
2. Setting Up the KIND Cluster with config-file.yaml
Create a kind-cluster-config.yaml file
```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4

nodes:
- role: control-plane
  image: kindest/node:v1.31.2
- role: worker
  image: kindest/node:v1.31.2
- role: worker
  image: kindest/node:v1.31.2
```
Create the cluster using the configuration file:
```
kind create cluster --name my-kind-cluster --config kind-cluster-config.yaml 
```
# To install nginx ingress controller
```
kubectl apply -f https://kind.sigs.k8s.io/examples/ingress/deploy-ingress-nginx.yaml
```













