# 📊 Kubernetes Monitoring Dashboard using Grafana + Prometheus
![Screenshot 2025-04-12 at 22 32 20](https://github.com/user-attachments/assets/05b49153-11dd-402f-8fd6-4039ab008ee5)

A robust, production-ready monitoring dashboard for Kubernetes clusters. This setup includes:
- 3 Namespaces: `ns1`, `ns2`, and `ns3`
- 12 Pods total (4 per namespace) created using Kubernetes Deployments
- Prometheus for metric scraping
  <img width="1428" alt="Screenshot 2025-04-12 at 20 28 41" src="https://github.com/user-attachments/assets/e7cbd630-1510-49fe-a20a-a8efb6802794" />
<img width="1440" alt="Screenshot 2025-04-12 at 20 28 25" src="https://github.com/user-attachments/assets/6acd4864-a50c-45d8-91c1-a8ddd2cd0a8f" />
<img width="1434" alt="Screenshot 2025-04-12 at 20 28 05" src="https://github.com/user-attachments/assets/791c03f2-037b-4f17-b891-e690626a2db8" />

- Grafana for powerful visualization
  ![Screenshot 2025-04-12 at 22 33 27](https://github.com/user-attachments/assets/d2f019db-f102-4407-b0fb-ff66c37412f9)
![Screenshot 2025-04-12 at 22 33 07](https://github.com/user-attachments/assets/0ad9878d-0227-48a0-a893-6105ba654257)


---

## 🔥 Features

- 📍 Per-namespace monitoring (`ns1`, `ns2`, `ns3`)
- 📈 Pod-level resource usage: CPU, memory, network, restarts
- ⚡ Live metrics with Prometheus data source
- 🧠 Custom Grafana dashboard (JSON config included)

---

## 💠 Tech Stack

- Kubernetes (tested on v1.28+)
- Prometheus (via Helm)
- Grafana (via Helm)
- Helm 3
- YAML + Bash

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/k8s-grafana-monitoring-dashboard.git
cd k8s-grafana-monitoring-dashboard
```

### 2. Create Namespaces and Deploy Pods

```bash
kubectl create ns ns1 ns2 ns3
kubectl apply -f deployments/ns1-deployment.yaml -n ns1
kubectl apply -f deployments/ns2-deployment.yaml -n ns2
kubectl apply -f deployments/ns3-deployment.yaml -n ns3
```

### 3. Install Prometheus & Grafana using Helm

```bash
# Add repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# Install Prometheus
helm install prometheus prometheus-community/prometheus -n monitoring --create-namespace

# Install Grafana
helm install grafana grafana/grafana -n monitoring
```

### 4. Access Grafana UI

```bash
kubectl get svc -n monitoring  # Get the Grafana service (usually a NodePort or LoadBalancer)

# Default login
Username: admin
Password: prom-operator-generated-password
```

> To get the password:
```bash
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```

---

## 📁 Import Dashboard

- Go to Grafana → Dashboards → Import
- Upload `dashboards/k8s-dashboard.json`
- Choose Prometheus as the data source

---

## 📸 Dashboard Preview

| Namespace | Screenshot |
|----------|------------|
| `ns1`    | !(<img width="761" alt="Screenshot 2025-04-13 at 13 18 30" src="https://github.com/user-attachments/assets/432d70a8-b433-416a-acc9-7f1c1d59d36a" />) |
| `ns2`    | !(<img width="783" alt="Screenshot 2025-04-13 at 13 18 45" src="https://github.com/user-attachments/assets/25a9b978-da19-4dc3-bf49-3edf753a057b" />) |
| `ns3`    | !(<img width="742" alt="Screenshot 2025-04-13 at 13 19 03" src="https://github.com/user-attachments/assets/05b9064c-70e7-44f9-92e0-8a65b949ed7d" />) |

---

## 🔄 Teardown (Optional)

```bash
./scripts/cleanup.sh
```

---

## 🙌 Contributing

Feel free to fork, star, or open a PR to contribute to this project!

---



## 🔗 Links

- 🔗 [Ambati Bhargavi – LinkedIn](https://www.linkedin.com/in/ambatibhargavi/)
- 💻 [GitHub](https://github.com/ambatibhargavi)
  
<img width="785" alt="Screenshot 2025-04-09 at 08 23 30" src="https://github.com/user-attachments/assets/7b629bab-462b-449c-b5bc-7c8901b3cc08" />
<img width="1083" alt="Screenshot 2025-04-12 at 20 18 26" src="https://github.com/user-attachments/assets/1850efb8-30e1-49bb-b165-f8c4e5137cf7" />
<img width="773" alt="Screenshot 2025-04-12 at 20 18 16" src="https://github.com/user-attachments/assets/654956af-6cfe-44a0-bae6-b0de9384024e" />
<img width="556" alt="Screenshot 2025-04-12 at 20 17 46" src="https://github.com/user-attachments/assets/a710eec4-eb62-4fd9-8bfe-460cdcc0c88c" />
<img width="653" alt="Screenshot 2025-04-12 at 20 17 32" src="https://github.com/user-attachments/assets/07a05b36-9064-4fc3-901a-e813a8aee85d" />
<img width="563" alt="Screenshot 2025-04-09 at 08 30 18" src="https://github.com/user-attachments/assets/51f78992-dde5-4935-9f07-e13e0a5b2795" />
<img width="800" alt="Screenshot 2025-04-09 at 08 29 09" src="https://github.com/user-attachments/assets/7cb07ca4-4df6-41a1-81c4-bd4632f9d472" />

