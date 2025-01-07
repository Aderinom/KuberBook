# Kubernetes Nomenclature

Kubernetes, often abbreviated as K8s, has its own unique terminology. Understanding this nomenclature is crucial for working with Kubernetes effectively. Here's a breakdown of key terms:

## Core Concepts - Hardware Abstraction

- **Cluster**: A set of nodes (servers) for running containerized applications. It's the foundation of Kubernetes.
- **Node**: A worker machine in Kubernetes, part of a cluster. Can be a physical or virtual machine.

## Core Concepts - Application Abstraction

- **[Container](https://kubernetes.io/docs/concepts/containers/)**: Can be seen as a super lightweight VM which contains an application.
- **[Pod](https://kubernetes.io/docs/concepts/workloads/pods/)**: The smallest deployable unit in K8. It can contain one or more containers with shared storage and network resources. A pod is always on one node
- **[WorkLoad](https://kubernetes.io/docs/concepts/workloads/controllers/)**:  A workload is an application running on Kubernetes, it can be scaled, updated, etc. There are multiple differnt kinds of workloads:
  - **Deployment**: A Stateless Workload (e.g. Ngnix serving a webpage)
  - **StatefulSet**: A Stateful Workload (e.g. a Database)
  - **Daemon Sets**: Something running on the Node - e.g. a Metrics Collector
  - **Job/CronJob**: A One off or scheduled Task 

## Core Concepts - Network Abstraction

- **Network Policy**: Network Rules, Kinda like a Cluster IPTables
- **Service (Layer3)**: Layer 3 Networking rules - assings internal or external IPs to Pods. Can also support Layer7 routing
- **Ingress (Layer7)**: Connects Services to the Outside world through HTTP/S (can also support Layer3), uses ingress Controller which are addons to a Kubernetes cluster.
- **Gateway API (Layer 7 & 3)**: Upcoming api to replace Ingress. requires a Gateway Controller which are addons to the Kubernetes Cluster.

## Core Concepts - Resource Organization

- **Namespace**: A virtual cluster within a physical Kubernetes cluster. Can contain most other resources avaiable. Useful for Oranizing, creating Resource restrictions, access restrictions etc.

## Core Concepts - Graph

![CoreConcepts](./01-KubeCoreConcepts.drawio.svg)
