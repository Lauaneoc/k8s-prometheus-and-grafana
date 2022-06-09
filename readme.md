Esse repositório coleta manifestos do Kubernetes, painéis do Grafana e regras do Prometheus combinados com documentação e scripts para fornecer monitoramento de cluster do Kubernetes de ponta a ponta, fácil de operar com Prometheus, usando o *Prometheus Operator*. Implementaremos facilmente o Prometheus e o Grafana usando o gráfico Helm para o Operador do Prometheus.

# Prometheus
um sistema de coleta de métricas de aplicações e serviços para armazenamento em um banco de dados de séries temporais.

# Grafana
O Grafana é uma plataforma para visualizar e analisar métricas por meio de gráficos. 

### Pré requisitos:
- helm instalado
- Kubernetes 

# HELM

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh 
```
Ou, se preferir outras formas de instalação, segue o link da documentação: https://helm.sh/docs/intro/install/

# Prometheus(Install)

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack
```
## Resumo dos comandos executados:

 * Pilha de monitoramento;
 * Configuração do seu cluster Kubernetes;
   - Worker Nodes monitorado;
   - Componentes do k8s monitorado.

### Para acessar o Grafana por localhost:
```
kubectl logs prometheus-grafana-9ff5889f4-qhfd8 
kubectl logs prometheus-grafana-9ff5889f4-qhfd8 -c grafana
kubectl port-forward deployment/prometheus-grafana 3000
```

*Inicie seu browser: localhost:3000/*
_user: admin_
_password: prom-operator_

### Para acessar Prometheus por localhost:
```
kubectl port-forward prometheus-prometheus-kube-prometheus-prometheus-0 9000
```

*Inicie seu browser: localhost:9090/*

# Dashboard no Grafana

A partir do momento que você inicia o prometheus e o grafana, já tem alguns dashboards configurados para visualização.

### Dashboards exemplos:

![exemplo](images/Captura%20de%20tela%20de%202022-06-09%2014-16-18.png)

*clique em DASHBOARD e você verá todos existentes no seu grafana*

Por outro lado, existem opções de personalizar um  dashboard de acordo com sua preferência, ou copiar repositórios prontos.
 Neste link você encontra várias opções de dashboards prontos
para uso: https://grafana.com/grafana/dashboards/





