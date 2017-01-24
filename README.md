# Getting started with Kubernetes

Kubernetes is a tool that takes linux containers and deploy them in distributed system. So you can run large number of containers in production and scale them up. It supports multiple cloud providers as AWS, Azure, Google Cloud Platform ...etc

Linux container is packaging mechanism, it provides to developers many powerful features as portability, isolation, security...

Docker has solved the problem of packaging, deploying and running containerized applications. It's great for managing few containers running on a fewer machines.

Production applications deal with dozens of containers running on hundreds of machines.

Docker is a phenomenal tool for managing and running one or multiple containers on one host

## Cluster Manager / Orchestration Engine

- Docker Swarm
- Kubernetes
- Mesossphere OS/DC

## What is Kuberenetes ?

- Open source project inspired from an internal Google project called Borg (subset of it)
- Decouples applications from machines through containers
- APIs for deployment workflows:
  - Rolling updates
  - Canary deploys
  - Blue-green deployments
  
## Kubernetes Architecture

<img src="architecture.png" width="50%"/>

Master-Slave design, the user submit the container definition (in YAML or JSON file) to the master through:

- API
- UI
- CLI

The container definition container the image container, constraints, affinity, ports, volumes ...etc

## Setup & configure Kuberenetes

- Minikube: simplest way to get Kubernetes cluster up and running
- Kubernetes Multi-Node Cluster: emulates production environment
- Google Container Engine

## Kubernetes Terminology

- Nodes: hosts that run kubeneretes applications
- Containers: Units of packaging
- Pods: Units of deployment (collection of container)
- Replication Controller: ensures availability and scalability
- Labels: Key-Value pairs for identification
- Services: collection of pods exposed as an endpoint

## List of commands

| Command        | Description  |
| ------------- |:-------------:|
| kubectl get nodes      | get list of nodes |
| kubectl get cs      | components health      |
| kubectl get pods | list of pods |
| kubectl config use-context "vagrant multi" | switch kube control to another cluster |
| kubectl expose deployment name --target-port= --type=NodePort | create a service |
| kubectl get services | get list of services |

## Kuberentes Master

- apiserver:
- scheduler:
- controller-manager:

## Kuberenetes Node

- kubelet: agent to interact with master and report health status & metrics to etcd
- kube-proxy: distributed network
- docker: linux container engine (see rkt)

### POD

- Group of one or more containers that are always co-located, co-scheduled and run in a shared context
- Each pod is isolated by:
  - process id namespace
  - network namespace
  - interprocess communication namespace
  - unix time sharing (uts) namespace
  
### Labels & Selectors

Assign meta-data

### Services

An abstraction to define a logical set of Pods. Services are exposed through internal and external endpoints

- Cluster IP: available only in the cluster
- NodePort: external service

### Replication Controller

Ensures that a Pod or set of Pods are always up and available, it always maintains desired number of Pods


## Deploy a 3-tier application



- Each pod gets a virtual IP (dynamic ip address)
- Service is kind of a proxy, with a fixed virtual ip address
- Each component deployed as a pod
- We use services for component communication
