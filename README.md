# Kubernetes Lab — NGINX

Este repositório é um **laboratório prático de Kubernetes** criado para demonstrar, na prática, conceitos fundamentais usados em ambientes DevOps e Cloud Native.

O objetivo é mostrar **boas práticas reais**, indo além de exemplos básicos, utilizando manifests declarativos (`.yaml`) versionados em Git.

---

## 🎯 Objetivos do Laboratório

* Criar e gerenciar recursos Kubernetes via YAML
* Entender a arquitetura **Ingress → Service → Pod**
* Aplicar boas práticas de **segurança**, **observabilidade** e **disponibilidade**
* Simular um cenário próximo de produção

---

## 🧱 Arquitetura

```
Usuário
   ↓
Ingress (nginx)
   ↓
Service (ClusterIP)
   ↓
Pods (NGINX)
```

---

## 📁 Estrutura do Repositório

```
kubernetes-lab/
├── namespace.yaml
├── nginx-configmap.yaml
├── nginx-deployment.yaml
├── nginx-service.yaml
├── nginx-ingress.yaml
└── README.md
```

---

## 📦 Recursos Kubernetes Utilizados

* **Namespace** — Isolamento lógico do ambiente
* **ConfigMap** — Configuração do NGINX desacoplada da imagem
* **Deployment** — Gerenciamento de réplicas e rollout
* **Service (ClusterIP)** — Comunicação interna no cluster
* **Ingress** — Exposição HTTP externa

---

## ⚙️ Boas Práticas Aplicadas

* Manifests declarativos versionados
* Healthchecks com **liveness** e **readiness probes**
* Controle de recursos (CPU e memória)
* Deploy sem downtime com **RollingUpdate**
* Container rodando como usuário não-root
* Separação clara de responsabilidades entre recursos

---

## 🚀 Como executar o laboratório

### 1️⃣ Pré-requisitos

* Kubernetes (Kind, Minikube, K3s ou cluster gerenciado)
* kubectl configurado
* Ingress Controller NGINX instalado

---

### 2️⃣ Criar os recursos

```bash
kubectl apply -f namespace.yaml
kubectl apply -f nginx-configmap.yaml
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml
kubectl apply -f nginx-ingress.yaml
```

---

### 3️⃣ Verificar os recursos

```bash
kubectl get all -n devops-lab
kubectl get ingress -n devops-lab
```

---

### 4️⃣ Testar a aplicação

```bash
curl http://<INGRESS_IP>/nginx
```

Ou pelo navegador:

```
http://<INGRESS_IP>/nginx
```

---

## ❤️ Health Check

O NGINX expõe um endpoint de saúde utilizado pelas probes:

```http
GET /health
```

Esse endpoint é usado para:

* **Liveness Probe** — verificar se o container está vivo
* **Readiness Probe** — verificar se o pod pode receber tráfego

---

## 📈 Próximos Passos (Evoluções Planejadas)

* Horizontal Pod Autoscaler (HPA)
* NetworkPolicy
* TLS no Ingress
* Monitoramento com Prometheus e Grafana
* CI/CD com GitHub Actions

---

## 👨‍💻 Autor

**Daniel Viana**
DevOps | Docker | Kubernetes | Cloud | CI/CD

🔗 GitHub: [https://github.com/danielviana2127](https://github.com/danielviana2127)
