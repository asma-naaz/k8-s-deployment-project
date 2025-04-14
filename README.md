# TASK-5

# Kubernetes Cluster Setup and Application Deployment with Scaling and Exposure

* The purpose of this project is to create and manage a Kubernetes (K8s) cluster, deploy an application (NGINX in this case), and scale the application using Kubernetes resources like Deployments and Services. This project also includes basic Kubernetes operations like managing pods, exposing services, and scaling deployments.

What is Kubernetes (K8s)?
Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications. It allows you to deploy applications across a cluster of machines and helps manage the containers running your app by providing features like automatic scaling, load balancing, and resource management.

# Steps and Updated YAML for the Project:

* Install Kubernetes (using kubeadm):
* First, set up a Kubernetes cluster using kubeadm on multiple machines or a single machine in a local setup.
* Initialize the Kubernetes master node with kubeadm init.
* Set up the kubeconfig file on the worker nodes to communicate with the master.

# Create a Deployment YAML File:

* A deployment manages a set of identical pods, ensuring that the specified number of pods are running at all times.
* The YAML file below defines the deployment of a simple NGINX web server.

![Screenshot 2025-04-14 171014](https://github.com/user-attachments/assets/86d80e5f-5b03-45d6-ab93-e44173b5c921)

# Create a Service YAML File:

* A service is used to expose the application to the outside world or within the cluster.
* This YAML file defines a service that exposes the NGINX web application.

![Screenshot 2025-04-14 171033](https://github.com/user-attachments/assets/f24ffa19-b6c2-495f-9f45-7080cc0239b1)


Apply the deployment.yaml and service.yaml using kubectl apply -f <filename>.

![Screenshot 2025-04-14 170949](https://github.com/user-attachments/assets/adcd6f05-3404-466d-b8a9-4700edb5ad43)

# Verify the deployment and service:

* kubectl get pods
* kubectl get svc
* Scale the Deployment:

Scaling the deployment increases or decreases the number of pods running.

* kubectl scale deployment firstdeployment --replicas=5

# Access the Application:

* To access the application from outside the cluster, you can use the LoadBalancer service created earlier or port-forward the service:

* kubectl port-forward service/nginx-service 8080:80
* Access the NGINX web page by going to http://localhost:8080.

Monitor and View Logs:

Use kubectl describe to get details about the deployment and view logs of a specific pod:

* kubectl describe deployment firstdeployment
* kubectl logs <pod-name>

# Conclusion:
This project demonstrates how to use Kubernetes to create a cluster, deploy applications using YAML files, expose them through services, scale deployments, and monitor the application. Kubernetes automates container orchestration, making it easier to manage applications at scale.

This approach ensures that your application is highly available, scalable, and easily maintainable across different environments.
