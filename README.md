
Observability Helm Demo
=======================

This umbrella Helm chart references official Grafana Labs charts for a local demo environment.
It is configured for Minikube/Kind and uses NodePort services for ease of access.

Files:
- Chart.yaml
- values.yaml
- dashboards/ (example Grafana dashboard JSONs)

Quick demo install (assuming helm and kubectl configured for your cluster):

1) Create namespace:
   kubectl create namespace observabilidad

2) Add Grafana Helm repo:
   helm repo add grafana https://grafana.github.io/helm-charts
   helm repo update

3) From this directory, fetch dependencies:
   helm dependency update .

4) Install the chart:
   helm install observability . -n observabilidad -f values.yaml

5) Find Grafana nodeport (example):
   kubectl get svc -n observabilidad | grep grafana

Grafana admin credentials:
- user: admin
- pass: admin

Notes:
- This is a demo configuration (persistence disabled). For production, enable persistence, use Ingress, TLS, and secure credentials.
