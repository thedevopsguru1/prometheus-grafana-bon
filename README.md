# prometheus-grafana


```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
```
helm repo add stable https://charts.helm.sh/stable
```

```
helm repo update
```
Service
```
kubectl port-forward deployment/prometheus-grafana 3000
```

Loadbalancer
```
helm install prometheus -n prometheus prometheus-community/kube-prometheus-stack --set alertmanager.enabled=false --set grafana.service.type=LoadBalancer
```
password
```
kubectl get secret prometheus-grafana -n prometheus -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
