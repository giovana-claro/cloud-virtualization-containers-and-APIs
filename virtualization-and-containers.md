# Containers

This week, you will learn to evaluate the correct workflows for virtual machines and containers and how to choose the appropriate solution for the task at end. You will also learn about the powerful container management service: Kubernetes. You will apply this knowledge to create a containerized web service and deploy it to a managed container service.

**Learning Objectives**
- Evaluate different virtualization abstractions.
- Build solutions with containers.
- Build solutions with virtual machines.

## Container vs Virtual Machine

A Virtual Machine has a full operating system cloned into a running application
  - Utilized in monolithic application
  - Lift and Shift

A **Container** is a subset of an operating system, only what is necessary for the application to work
  - Smaller process
  - Faster
  - DevOps compliant

Multiple VMs on a machine would use more memory, since each of them has to have their own operating system. When talking
about Containers, they use the host's operating system and each one isolates the dependencies for running the application.

## Container from Scratch

```
FROM python:3.7.3-stretch

# Working Directory
WORKDIR /app

# Copy source code to working directory
COPY . app.py /app/

# Install packages from requirements.txt
RUN pip install --upgrade pip &&\
    pip install --trusted-host pypi.python.org -r requirements.txt
```

# Kubernetes

Container orchestration:
  - High availability architecture
  - Auto-scaling
  - Rich Ecosystem
  - Service Discovery
  - Container health management
  - Secrets and configuration management

Ability to set up auto-scaling via Horizontal Pod Autoscale. It works by HPA control loop looking at different health metrics for the
system, like CPU and Memory.

**Kebernetes Hierarchy:** Inside a Kubernet cluster you can have multiple nodes and each node can have different Pods.
This pods have different IPs and get its own collection of Containers.

**Deploy App on GKE**

```
gcloud container clusters create cloud-kubernetes
```
