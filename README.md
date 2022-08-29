# prometheus-grafana
https://www.fosstechnix.com/install-prometheus-and-grafana-on-kubernetes-using-helm/


Use this: https://www.infracloud.io/blogs/prometheus-operator-helm-guide/

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

Install & Loadbalancer
```
helm install prometheus -n prometheus prometheus-community/kube-prometheus-stack --set alertmanager.enabled=false --set grafana.service.type=LoadBalancer
```
password
```
kubectl get secret prometheus-grafana -n prometheus -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
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
