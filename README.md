# Kubernetes Lab — NGINX

Este repositório é um **laboratório prático de Kubernetes** criado para demonstrar, na prática, conceitos fundamentais usados em ambientes DevOps e Cloud Native.

O objetivo é mostrar **boas práticas reais**, indo além de exemplos básicos, utilizando manifests declarativos (`.yaml`) versionados em Git.

---

## 🎯 Objetivos do Laboratório

* Criar e gerenciar recursos Kubernetes via YAML
* Entender a arquitetura **Ingress → Service → Pod**
* Aplicar boas práticas de **segurança**, **observabilidade** e **disponibilidade**
* Simular um cenário próximo de produção
=======
# Kubernetes Lab — Nginx com Ingress, TLS e Boas Práticas

Este repositório contém um **laboratório prático de Kubernetes**, focado em expor uma aplicação **Nginx** via **Ingress Controller com TLS**, aplicando **boas práticas reais de produção**.

O projeto foi construído para simular problemas e soluções comuns do dia a dia DevOps, indo além de tutoriais básicos.

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
=======
**Componentes utilizados:**

* Kubernetes (Minikube)
* Nginx
* Ingress Controller (ingress-nginx)
* TLS (certificado self-signed)
* ConfigMap
* Healthcheck `/health`
* HPA (Horizontal Pod Autoscaler)
* NetworkPolicy

**Fluxo de tráfego:**

```
Usuário → Ingress (HTTPS) → Service → Pods (Nginx)
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
=======
.
├── configmap
│   └── nginx-configmap.yaml
├── deployment
│   └── nginx-deployment.yaml
├── hpa
│   └── nginx-hpa.yaml
├── ingress
│   └── nginx-ingress.yaml
├── namespace
│   └── namespace.yaml
├── secret
│   └── nginx-tls-secret.yaml
├── security
│   └── networkpolicy-nginx.yaml
└── service
    └── nginx-service.yaml
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

=======
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
=======
* Docker
* Minikube
* kubectl

---

### 2️⃣ Iniciar o cluster

```bash
minikube start
minikube addons enable ingress
```

Em outro terminal (obrigatório para LoadBalancer):

```bash
minikube tunnel
```

---

### 3️⃣ Verificar os recursos

```bash
kubectl get all -n devops-lab
=======
### 3️⃣ Criar o namespace

```bash
kubectl apply -f namespace/namespace.yaml
```

---

### 4️⃣ Criar o Secret TLS

O secret é criado a partir de um certificado local (self-signed).

```bash
kubectl apply -f secret/nginx-tls-secret.yaml
```

---

### 5️⃣ Aplicar ConfigMap e Deployment

```bash
kubectl apply -f configmap/nginx-configmap.yaml
kubectl apply -f deployment/nginx-deployment.yaml
```

Verificar rollout:

```bash
kubectl rollout status deployment nginx-deployment -n devops-lab
```

---

### 6️⃣ Criar o Service

```bash
kubectl apply -f service/nginx-service.yaml
```

---

### 7️⃣ Criar o Ingress

```bash
kubectl apply -f ingress/nginx-ingress.yaml
```

---

### 8️⃣ Ajustar o arquivo `/etc/hosts`

Adicionar a entrada:

```
<IP_DO_MINIKUBE> nginx.devops.lab
```

O IP pode ser obtido com:

```bash
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
=======
## 🔍 Testes

### Página principal

```bash
curl -k https://nginx.devops.lab/
```

### Healthcheck

```bash
curl -k https://nginx.devops.lab/health
```

Resposta esperada:

```
OK
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
=======
## 🧠 Boas práticas aplicadas

* ❌ Não sobrescrever `/etc/nginx/nginx.conf`
* ✅ Uso correto de `/etc/nginx/conf.d/default.conf`
* ✅ ConfigMap montando arquivo específico
* ✅ Healthcheck alinhado com liveness/readiness probes
* ✅ TLS configurado no Ingress
* ✅ Namespace isolado
* ✅ NetworkPolicy aplicada
* ✅ HPA configurado
* ✅ Requests e limits definidos

---

## 📈 Próximos passos (roadmap)

* [ ] Cert-manager
* [ ] Monitoramento com Prometheus
* [ ] Logs centralizados
* [ ] GitOps com ArgoCD

---

## 💼 Objetivo do Projeto

Este laboratório faz parte do meu **plano de estudos em DevOps**, com foco em Kubernetes, troubleshooting e boas práticas utilizadas em ambientes reais de produção.

---

📌 **Autor:** Daniel Viana