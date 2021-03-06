# Metric server is required for Horizontal Pod Autoscaler

## What is Metric Server?
```sh
It collects metrics like CPU, memory or Disk IO consumption for containers or nodes, from the Summary API, exposed by Kubelet on each node.
The Kubernetes Metrics Server is an aggregator of resource usage data in k8s cluster and used by k8s add ons, such as the Horizontal Pod Autoscaler or the Kubernetes Dashboard.
```

## Enable 4443 port on Master and Worker Nodes
```sh
4443
```
## Installation via components.yaml manifest
```sh
#Source -> https://github.com/kubernetes-sigs/metrics-server
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

## Installation via local copy
```sh
git clone https://github.com/kubernetes-sigs/metrics-server.git
#git clone https://github.com/prawinkorvi/metric-server.git
#git clone https://github.com/initsixcloud/metric-server.git
cd metric-server/deploy/1.8+
kubectl create -f .
```

## HELM way
```sh
#Source -> https://artifacthub.io/packages/helm/metrics-server/metrics-server
#Add the metrics-server repo to helm:
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
helm upgrade --install metrics-server metrics-server/metrics-server
```
## Test
```sh
kubectl get deployment metrics-server -n kube-system
kubectl top pods
kubectl top nodes
```

