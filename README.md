# Kubernetes Lab — NGINX com Ingress, TLS e Boas Práticas

Este repositório é um **laboratório prático de Kubernetes** com foco em boas práticas de organização, segurança e observabilidade. O projeto implementa uma aplicação **NGINX** exposta via **Ingress Controller**, com **TLS**, **HPA**, **ConfigMap**, **NetworkPolicy** e separação clara de manifests.

> Objetivo: demonstrar domínio dos fundamentos de Kubernetes em um cenário realista, organizado e reproduzível.

---

## 🧱 Tecnologias Utilizadas

* Kubernetes (testado com **Minikube**)
* NGINX
* NGINX Ingress Controller
* TLS (Secret)
* HPA (Horizontal Pod Autoscaler)
* NetworkPolicy

---

## 📁 Estrutura do Projeto

```text
kubernetes-lab/
├── namespace/
│   └── namespace.yaml
├── configmap/
│   └── nginx-configmap.yaml
├── deployment/
│   └── nginx-deployment.yaml
├── service/
│   └── nginx-service.yaml
├── ingress/
│   └── nginx-ingress.yaml
├── hpa/
│   └── nginx-hpa.yaml
├── secret/
│   └── nginx-tls-secret.yaml
├── security/
│   └── networkpolicy-nginx.yaml
└── README.md
```

### 📌 Organização

* Cada diretório representa **uma responsabilidade do Kubernetes**
* Facilita manutenção, leitura e versionamento
* Estrutura comum em ambientes profissionais

---

## 🚀 Como Executar o Projeto

### 1️⃣ Criar o namespace

```bash
kubectl apply -f namespace/namespace.yaml
```

### 2️⃣ Criar o ConfigMap do NGINX

```bash
kubectl apply -f configmap/nginx-configmap.yaml
```

### 3️⃣ Criar o Secret TLS

```bash
kubectl apply -f secret/nginx-tls-secret.yaml
```

### 4️⃣ Subir o Deployment e o Service

```bash
kubectl apply -f deployment/nginx-deployment.yaml
kubectl apply -f service/nginx-service.yaml
```

### 5️⃣ Criar o Ingress

```bash
kubectl apply -f ingress/nginx-ingress.yaml
```

### 6️⃣ Aplicar HPA (opcional)

```bash
kubectl apply -f hpa/nginx-hpa.yaml
```

### 7️⃣ Aplicar NetworkPolicy (opcional)

```bash
kubectl apply -f security/networkpolicy-nginx.yaml
```

---

## 🌐 Acesso à Aplicação

Após subir o Ingress Controller e configurar o `/etc/hosts`:

```text
<IP_DO_CLUSTER> nginx.devops.lab
```

Acesse:

* HTTPS: `https://nginx.devops.lab/`
* Healthcheck: `https://nginx.devops.lab/health`

> Em ambiente local, pode ser necessário usar `minikube tunnel`.

---

## 🔐 Segurança

* Comunicação HTTPS via TLS
* NetworkPolicy restringindo acesso aos pods
* Recursos limitados por requests/limits

---

## 📈 Escalabilidade

* HPA configurado com base em CPU
* Permite escalar automaticamente os pods NGINX

---

## 📚 Aprendizados Demonstrados

* Organização profissional de manifests Kubernetes
* Uso correto de ConfigMap sem sobrescrever `nginx.conf`
* Exposição segura via Ingress + TLS
* Troubleshooting de rollout e permissões
* Git workflow com rebase e resolução de conflitos

---

## 📌 Próximos Passos

* Adicionar métricas com Prometheus
* Integrar com Grafana
* Criar pipeline CI/CD

---

## 👤 Autor

**Daniel Viana**
Estudante de DevOps | Kubernetes | Docker | Cloud

---

⭐ Se este projeto te ajudou ou serviu como referência, deixe uma estrela!

