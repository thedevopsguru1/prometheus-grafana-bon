# Prometheus & Grafana
## 1- Installing helm3 in kubernetes
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
```
```
chmod 700 get_helm.sh
```
```
./get_helm.sh
```
### Check helm version
```
helm version
```
## 2- Install prometheus and grafana on k8s using helm3

### Add the latest helm repository in Kubernetes
```
helm repo add stable https://charts.helm.sh/stable
```
### Add the Prometheus community helm chart in Kubernetes
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
### create prometheus namespace
```
kubectl create ns prometheus
```
### Installing prometheus & grafana to kubernetes
```
helm install prometheus prometheus-community/kube-prometheus-stack -n prometheus
```




Grafana Dashboard ID
# 1-pods
```
1471
```
# 2- 
```
https://blog.lwolf.org/post/going-open-source-in-monitoring-part-iii-10-most-useful-grafana-dashboards-to-monitor-kubernetes-and-services/
```
