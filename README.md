# Overall architecture

# Summary
This is a proof of concept for a microservice distributed system running on k8s. 
I will use it as a sandbox to test different deployment methods. 

![Interaction Diagram](./diagrams/interactions.png)

## Tooling
- Gitlab & runners
- Google Kubernetes Engine (GKE)
- PlantUML (Alt D to use on vscode)

# Microservices

## 1. HTTP ingress proxy
Lightweight API written in python (Flask). It receives http POST and GET requests and publishes to NATS 

## 2. NATS Core
NATS Core is a lightweight Pub Sub streaming services

## 3. Python Worker
The python worker subscribes to NATS and responds accordingly.

## 4. Python API
The python API is a Flask API which simulates talking to another system. It will take between 0.01-0.99 seconds to respond to a get request.