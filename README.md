# kindk8scluster
Create a virtualized multi node kubernetes cluster on your host machine using kind


## Prerequisites 

## Helm
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

## Kind
```
$(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

## Kubectl
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl 
mv kubectl /usr/local/bin/
sudo mv kubectl /usr/local/bin/
kubectl version --client

```
## Docker
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh 

```
### Docker post instalation steps 
```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
sudo systemctl enable docker
```

## Git
```
sudo apt-get install -y git 
```


## Clone this repository and Create a multi Node kubernetes cluster with exposed NodePort for public access 
```
git clone https://github.com/samuelbickersteth/kindk8scluster
cd kindk8scluster
kind create cluster --config multi-node.yaml --name multinodecluster

```
## Wait for few minutes and make sure all nodes are up and read 

```
kubectl get nodes 
```

## Deploy nginx pod and service with port 30012 exposed for Nginx with Custom webpage. 

```
cd deployment
kubectl apply -f nginxpod.yaml
kubectl apply -f svc.yaml

```

