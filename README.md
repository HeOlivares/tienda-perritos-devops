# Tienda Perritos - Despliegue DevOps en AWS EKS

## Descripción

Este proyecto implementa el despliegue de una aplicación web llamada Tienda Perritos utilizando una arquitectura DevOps sobre AWS. La solución contempla infraestructura como código con CloudFormation, construcción de imágenes Docker, almacenamiento en Amazon ECR, despliegue en Amazon EKS, escalamiento automático mediante HPA y automatización CI/CD con GitHub Actions.

## Arquitectura

La aplicación está compuesta por tres servicios principales:

- Frontend: aplicación web estática servida mediante Nginx.
- Backend: API desarrollada en Node.js con Express.
- Base de datos: MySQL desplegada dentro del clúster Kubernetes.

El acceso público se realiza mediante un Service de tipo LoadBalancer asociado al frontend. El backend y la base de datos se comunican internamente dentro del namespace `tienda`.

## Servicios AWS utilizados

- Amazon VPC
- Subredes públicas y privadas
- Internet Gateway
- NAT Gateway
- Amazon EKS
- Managed Node Group
- Amazon ECR
- CloudFormation
- CloudWatch / Metrics Server

## Contenedores

El proyecto construye y publica tres imágenes Docker en Amazon ECR:

- `tienda-frontend`
- `tienda-backend`
- `tienda-db`

## Kubernetes

Los manifiestos Kubernetes se encuentran en la carpeta `k8s/` e incluyen:

- Namespace
- Deployments
- Services
- Secret para MySQL
- Horizontal Pod Autoscaler para frontend
- Horizontal Pod Autoscaler para backend

## Despliegue manual

Para desplegar manualmente desde CloudShell:

```bash
chmod +x deploy.sh
./deploy.sh
