# Kubernetes Lab — Deploy de Aplicação em Kubernetes

Este repositório contém um laboratório prático de Kubernetes que demonstra o deploy de uma aplicação containerizada utilizando manifests YAML.

O projeto simula um fluxo básico de deploy em Kubernetes, cobrindo desde a criação dos recursos até a validação da aplicação em execução, como esperado no dia a dia de um **DevOps Júnior**.

---

## 🎯 Objetivo do Projeto

Demonstrar, de forma prática, os principais conceitos iniciais de Kubernetes, incluindo:

* Deploy de aplicações em Kubernetes
* Uso de manifests YAML
* Gerenciamento de Pods com Deployment
* Exposição de aplicações com Service
* Uso de ConfigMap para configuração
* Operação básica de um cluster Kubernetes local

---

## 🧰 Tecnologias Utilizadas

* Kubernetes
* kubectl
* Docker
* YAML
* Minikube

---

## 🏗️ Arquitetura da Aplicação

A aplicação é composta por:

* Aplicação Web containerizada
* Deployment para gerenciamento dos Pods
* Service para exposição da aplicação
* ConfigMap para configuração

Fluxo simplificado:

Usuário → Service → Pod (Aplicação)

---

## 🚀 Como Executar o Projeto

### Pré-requisitos

* Docker
* kubectl
* Minikube

---

### Subir o Cluster Kubernetes

```bash
minikube start
```

Verifique se o cluster está ativo:

```bash
kubectl get nodes
```

---

### Clonar o Repositório

```bash
git clone https://github.com/danielviana2127/kubernetes-lab.git
cd kubernetes-lab
```

---

### Aplicar os Manifests Kubernetes

```bash
kubectl apply -f k8s/
```

---

### 🔹 Verificar os Recursos Criados

Verifique se os Pods estão rodando:

```bash
kubectl get pods
```

Verifique o Service:

```bash
kubectl get svc
```

Os Pods devem estar com status **Running**.

---

### 🔹 Acessar a Aplicação

#### Opção 1 — Port Forward (mais simples)

```bash
kubectl port-forward svc/nome-do-service 8080:80
```

Acesse no navegador:

```
http://localhost:8080
```

#### Opção 2 — Minikube Service

```bash
minikube service nome-do-service
```

O Minikube abrirá automaticamente a aplicação no navegador.

---

## 🔄 Operações Básicas com kubectl

Durante o uso do Kubernetes, os comandos abaixo são comuns para inspeção e troubleshooting:

```bash
kubectl describe pod <nome-do-pod>
kubectl logs <nome-do-pod>
```

Para remover todos os recursos criados pelo laboratório:

```bash
kubectl delete -f k8s/
```

---

## 📚 Aprendizados

* Deploy e operação básica de aplicações em Kubernetes
* Escrita e aplicação de manifests YAML
* Gerenciamento de Pods e Services
* Validação de aplicações em execução
* Troubleshooting básico com kubectl

---

## 👤 Autor

Daniel Viana
🔗 LinkedIn: [https://www.linkedin.com/in/daniel-viana-a9556669/](https://www.linkedin.com/in/daniel-viana-a9556669/)