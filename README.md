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


## Accessing Prometheus
### Look for Services:
```
kubectl get svc -n prometheus
```
### Look for "prometheus-kube-prometheus-prometheus" and select the "EXTERNAL-IP" and the port 9090
### Paste on the browser
![image](https://user-images.githubusercontent.com/107158398/187271606-343040ac-8c36-4ef7-96a0-7ab576d281a2.png)
### Let play a little bit with prometheus.
## As you can see prometheus UI is not user friendly.
## to fix this , we can use user friendly UI ,named Grafana.
### Accessing Grafana
### Look for Services:
```
kubectl get svc -n prometheus
```
### Look for "prometheus-grafana" and select the "EXTERNAL-IP" and the port 80
![image](https://user-images.githubusercontent.com/107158398/187272352-50eddd7e-86a1-4a25-8735-9929397ae806.png)

### Paste on the browser
![image](https://user-images.githubusercontent.com/107158398/187272460-ed162491-0674-41c3-bfda-dcbed970ba66.png)

#### Username: 
```
admin
```
#### Password:
```
prom-operator
```
![image](https://user-images.githubusercontent.com/107158398/187272824-82ee5abf-7bbb-4566-b1f6-539d00c82462.png)

### Let create a dashbord to see kubernetes objects( pods, services, ...)
#### click on dashbord , then import.
![image](https://user-images.githubusercontent.com/107158398/187273215-30a1ed69-5b42-431c-bce1-24af17a77b59.png)
#### On Import via grafana.com put 741 and click on load
![image](https://user-images.githubusercontent.com/107158398/187273449-4f52ed35-8dc0-4c78-884e-21ffd29924f5.png)
#### Prometheus at the bottom  , select "Prometheus"
![image](https://user-images.githubusercontent.com/107158398/187273656-d335f971-4e2f-427f-b006-0dbd95d6e99e.png)
#### then click on Import
![image](https://user-images.githubusercontent.com/107158398/187273729-9e41634f-5d24-4ede-990c-a9656a326cc9.png)


# Grafana Dashboard ID
### Please , if you need more Dashboard ID , use the link below
```
https://blog.lwolf.org/post/going-open-source-in-monitoring-part-iii-10-most-useful-grafana-dashboards-to-monitor-kubernetes-and-services/
```
### Let try some of them:
```
9797
```
```
11670
```
