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

### Check if we have deployed all
```
kubectl get all -n prometheus
```
#### We should see a lot of objects.
### Edit prometheus service to Loadbalancer
```
kubectl edit svc prometheus-kube-prometheus-prometheus -n prometheus
```
#### click I then edit it by changer type: clusterIP to LoadBalancer
![image](https://user-images.githubusercontent.com/107158398/187269632-0a8aa705-7b1a-44dd-939b-5eb64299d891.png)

### Edit grafana service to Loadbalancer
```
kubectl edit svc prometheus-grafana -n prometheus
```
#### click I then edit it by changer type: clusterIP to LoadBalancer







Grafana Dashboard ID
# 1-pods
```
1471
```
# 2- 
```
https://blog.lwolf.org/post/going-open-source-in-monitoring-part-iii-10-most-useful-grafana-dashboards-to-monitor-kubernetes-and-services/
```
