 Esse repositório coleta manifestos do Kubernetes painéis do Grafana e regras do Prometheus combinados com documentação e scripts para fornecer monitoramento de cluster do Kubernetes de ponta a ponta fácil de operar com Prometheus usando o Prometheus Operator. Implementaremos facilmente o Prometheus e o Grafana usando o gráfico Helm para o Operador do Prometheus.

# Prometheus


# Grafana


## Pré requisitos:
- helm instalado
- Kubernetes 

## HELM

```curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh 
```
Ou, se preferir outras formas de instalação, segue o link da documentação: https://helm.sh/docs/intro/install/

## Prometheus(Install)

```helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack
```
# Resumo dos comandos executados:

 * Pilha de monitoramento;
 * Configuração do seu cluster Kubernetes;
   - Worker Nodes monitorado;
   - Componentes do k8s monitorado.

### Para acessar o Grafana por localhost:
```kubectl logs prometheus-grafana-9ff5889f4-qhfd8 
kubectl logs prometheus-grafana-9ff5889f4-qhfd8 -c grafana
kubectl port-forward deployment/prometheus-grafana 3000
```

*Inicie seu browser: localhost:3000/*

### Para acessar Prometheus por localhost:
```kubectl port-forward prometheus-prometheus-kube-prometheus-prometheus-0 9000
```

*Inicie seu browser: localhost:9090/*
