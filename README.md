# prometheus-lab
Baby steps with Prometheus and Graphana

# Pre-requisites

- Kubernetes cluster
- Helm 3.0++

# Add Helm's default chart repository

```bash
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
```

# Install Prometheus using Helm

## Inspect Prommetheus Chart

Suggest taking a look at the values.yaml file to get a better understanding of deployment parameters:

```bash
helm repo update && helm show values stable/prometheus | less
```

## Install Prometheus (without Alert Manager)

Execute:

```bash
kubectl create namespace monitoring && \
    helm install --set alertmanager.enabled=false prometheus stable/prometheus --namespace monitoring 
```

Wait for Prometheus pods to start:

```bash
kubectl get pod -w --namespace monitoring
```

# Install Grafana using Helm

## Inspect Grafana Chart

Suggest taking a look at the values.yaml file to get a better understanding of deployment parameters:

```bash
helm repo update && helm show values stable/grafana | less
```

## Install Graphana

Execute:

```bash
kubectl create namespace monitoring && \
    helm install --set alertmanager.enabled=false prometheus stable/prometheus --namespace monitoring 
```

Wait for Prometheus pods to start:

```bash
kubectl get pod -w --namespace monitoring
```