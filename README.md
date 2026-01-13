# ☸️ Kubernetes Lab – Deploy e Observabilidade

## 📌 Visão Geral

Este repositório é um **laboratório prático de Kubernetes**, criado para demonstrar a implantação e operação de um **serviço web containerizado** em um **cluster Kubernetes**, seguindo boas práticas utilizadas em ambientes DevOps.

O projeto evolui progressivamente desde o **deploy básico** até a **observabilidade**, simulando cenários comuns de ambientes reais.

---

## 🎯 Objetivos do Projeto

* Demonstrar domínio dos principais **recursos do Kubernetes**
* Realizar deploy de aplicações utilizando **manifests declarativos**
* Gerenciar configurações via **ConfigMaps** e **Secrets**
* Expor serviços de forma controlada
* Preparar o ambiente para **monitoramento e observabilidade**
* Consolidar conceitos fundamentais para atuação como **DevOps Júnior**

---

## 🧱 Arquitetura do Ambiente

Componentes planejados:

* **Namespace dedicado**
* **Deployment**

  * Aplicação NGINX
  * Gerenciamento de réplicas
* **Service**

  * Exposição interna (ClusterIP)
* **ConfigMap**

  * Configuração do NGINX
* **Secret**

  * Simulação de dados sensíveis
* **Ingress** (opcional)

  * Acesso externo ao serviço

Fluxo simplificado:

Usuário → Ingress → Service → Pod (NGINX)

---

## 🛠️ Tecnologias Utilizadas

* Kubernetes
* Docker
* NGINX
* YAML
* Linux

---

## 📂 Estrutura do Repositório (Planejada)

```
kubernetes-lab/
├── namespace/
│   └── namespace.yaml
├── deployment/
│   └── nginx-deployment.yaml
├── service/
│   └── nginx-service.yaml
├── configmap/
│   └── nginx-configmap.yaml
├── secret/
│   └── nginx-secret.yaml
├── ingress/
│   └── nginx-ingress.yaml
└── README.md
```

---

## ▶️ Como Executar (quando implementado)

### Pré-requisitos

* Kubernetes local (Minikube ou Kind)
* kubectl configurado

### Passos gerais

```bash
kubectl apply -f namespace/
kubectl apply -f configmap/
kubectl apply -f secret/
kubectl apply -f deployment/
kubectl apply -f service/
```

---

## 📊 Observabilidade (Fase futura)

Planejamento de evolução:

* Exposição de métricas da aplicação
* Integração com Prometheus
* Visualização com Grafana
* Criação de dashboards básicos

---

## 🔐 Boas Práticas Aplicadas

* Manifests declarativos versionados
* Separação de responsabilidades
* Uso de namespaces
* Simulação segura de segredos
* Facilidade de reprodução do ambiente

---

## 📈 Evoluções Planejadas

* Autoscaling (HPA)
* Liveness e Readiness Probes
* Resource requests e limits
* Integração com CI/CD
* Observabilidade completa

---

## 👤 Autor

**Daniel Viana**
DevOps Júnior | Infraestrutura | Kubernetes | Observabilidade

* LinkedIn: [https://www.linkedin.com/in/danielvianasilva](https://www.linkedin.com/in/danielvianasilva)
* GitHub: [https://github.com/danielviana2127](https://github.com/danielviana2127)

---

> Laboratório desenvolvido para consolidar conhecimentos práticos em Kubernetes, com foco em ambientes reais e boas práticas DevOps.
