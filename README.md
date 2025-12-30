# Zabbix Server + MySQL Stack

This repository provides configuration for deploying **Zabbix Server with a MySQL backend**.
It is suitable for Kubernetes or container-based environments and is designed to be customized
through `values.yaml`.

---

## 📦 Components

- **Zabbix Server (MySQL)**
- **MySQL Database**
- **Zabbix Web UI**
- Optional Ingress and persistent storage

---

## 🧰 Prerequisites

- Kubernetes cluster
- Helm 3.x
- kubectl configured
- Persistent storage support (recommended)

---

## 🚀 Deployment with Helm
### 2. Deploy Zabbix using custom values

```bash
helm upgrade --install zabbix zabbix-stack \
  --namespace monitoring \
  --create-namespace \
  -f values.yaml
```

---

## ⚙️ Configuration Highlights

### Zabbix Server Image

```yaml
zabbixServer:
  image:
    repository: zabbix/zabbix-server-mysql
    tag: latest
```

### Database Configuration

```yaml
mysql:
  enabled: true
  mysqlUser: zabbix
  mysqlPassword: zabbix
  mysqlDatabase: zabbix
```

### Web UI

```yaml
zabbixWeb:
  enabled: true
```

### Ingress (optional)

```yaml
ingress:
  enabled: true
  hosts:
    - host: zabbix.example.com
      paths:
        - /
```

---

## 🔐 Default Login

- **Username:** Admin
- **Password:** zabbix

⚠️ Change credentials immediately after first login.

---

## 🧹 Uninstall

```bash
helm uninstall zabbix -n monitoring
kubectl delete namespace monitoring
```

---

## 📚 References

- https://www.zabbix.com
- https://zabbix-community.github.io/helm-zabbix

---

## 🧑‍💻 Maintainer

Trong Nguyen  
GitHub: https://github.com/trongkido
