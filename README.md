# Kubernetes YAML Manifest Basics

## **Introduction**
In this tutorial, we will learn how to define Kubernetes resources using **YAML manifests**. Instead of running commands manually, YAML allows us to define configurations that can be applied consistently.

---

## **1️⃣ Writing a Pod YAML File**
### **pod.yaml**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
  labels:
    app: myapp
spec:
  containers:
    - name: nginx-container
      image: nginx:latest
      ports:
        - containerPort: 80
```
### **Apply the Pod configuration**
```sh
kubectl apply -f pod.yaml
```
### **Verify the Pod**
```sh
kubectl get pods
```

---

## **2️⃣ Writing a Deployment YAML File**
### **deployment.yaml**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
  labels:
    app: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
        - name: nginx-container
          image: nginx:latest
          ports:
            - containerPort: 80
```
### **Apply the Deployment**
```sh
kubectl apply -f deployment.yaml
```
### **Check Deployment Status**
```sh
kubectl get deployments
kubectl get pods
```

---

## **3️⃣ Writing a Service YAML File**
### **service.yaml**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: NodePort
```
### **Apply the Service**
```sh
kubectl apply -f service.yaml
```
### **Get Service Details**
```sh
kubectl get services
```
### **Access the Application**
```sh
minikube service myapp-service --url
```

---

## **🎥 Want to Learn More?**
Stay tuned for the next video where we'll cover **ConfigMaps & Secrets** to manage environment variables! 🚀

