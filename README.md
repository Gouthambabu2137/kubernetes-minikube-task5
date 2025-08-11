# Kubernetes Minikube Task 5

## Objective
Set up a local Kubernetes cluster using Minikube, deploy a containerized application, expose it via a service, and demonstrate scaling and monitoring.

---

## Tools and Technologies
- **Kubernetes** (via Minikube)
- **kubectl**
- **Docker**
- **YAML** for Kubernetes manifests

---

## Implementation Steps

### 1. Start Minikube
```bash`
minikube start --driver=docker
minikube status
2. Create Deployment
deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80

Apply:
kubectl apply -f deployment.yaml

3. Create Service
service.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  type: NodePort
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30007

Apply:
kubectl apply -f service.yaml

4. Verify Resources
kubectl get pods
kubectl get svc

5. Scale Deployment
kubectl scale deployment nginx-deployment --replicas=3
kubectl get pods

6. Inspect and Monitor
kubectl describe pod <pod-name>
kubectl logs <pod-name>

Screenshots
Verification outputs and steps are saved in the Screenshots/ folder:

Cluster status

Deployment

Pods list

Services list

Scaling result

Pod description


#Author#
Goutham Babu

Repository: kubernetes-minikube-task5Accessing the Application
