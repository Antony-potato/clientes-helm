# clientes-helm

Helm chart del proyecto integrador. Despliega MySQL, el backend y el frontend en un cluster Kubernetes local (Minikube).

## Requisitos

- Minikube
- kubectl
- Helm 3

## Configuración

Antes de instalar, edita [clientes-app/values.yaml](clientes-app/values.yaml) y cambia `dockerUser` y las imágenes:

```yaml
backend:
  image: TU_USUARIO_DOCKERHUB/clientes-back:latest

frontend:
  image: TU_USUARIO_DOCKERHUB/clientes-front:latest
```

## Instalación

```bash
minikube start

helm install clientes ./clientes-app

kubectl get pods
kubectl get svc

minikube service frontend-service
```

## Actualización

```bash
helm upgrade clientes ./clientes-app
```

## Desinstalar

```bash
helm uninstall clientes
kubectl delete pvc mysql-pvc
```

## Estructura

```
clientes-app/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── mysql-secret.yaml
    ├── mysql-initdb-configmap.yaml
    ├── mysql-pvc.yaml
    ├── mysql-deployment.yaml
    ├── mysql-service.yaml
    ├── backend-deployment.yaml
    ├── backend-service.yaml
    ├── frontend-deployment.yaml
    └── frontend-service.yaml
```
