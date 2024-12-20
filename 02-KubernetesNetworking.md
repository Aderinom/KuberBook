# Kubernetes Networking Components

## Service

- Provides a stable network endpoint for a set of Pods
- Operates at Layer 4 (TCP/UDP)
- Types: ClusterIP, NodePort, LoadBalancer, ExternalName

## Ingress

- Manages external access to Services in a cluster
- Operates at Layer 7 (HTTP)
- Provides HTTP/HTTPS routing
- Can provide SSL termination, name-based virtual hosting, and more

## Gateway API

- Manages external access to Services in a cluster
- Operates at Layer 3/7
- Provides HTTP/HTTPS routing
- More extensive feature set than Ingress - better support for TCP/UDP

## Network Policy

- Defines how groups of Pods are allowed to communicate with each other and other network endpoints
- Acts as a firewall for Pods
- Can restrict traffic based on namespaces, labels, IP blocks, and ports
- Is namespace-scoped

## Comparison

| Feature              | Service                     | Ingress                     | Gateway API                | Network Policy            |
|----------------------|-----------------------------|-----------------------------|----------------------------|---------------------------|
| Primary Function     | Expose Pods                 | Route external HTTP traffic | Advanced traffic routing   | Control Pod communication |
| Protocol             | Any (typically TCP/UDP)     | HTTP/HTTPS                  | HTTP/HTTPS, TCP, UDP, TLS  | Any                       |
| Layer                | 4                           | 7                           | 4-7                        | 3-4                       |
| Scope                | Cluster-wide                | Cluster-wide                | Cluster-wide               | Namespace                 |
| Load Balancing       | Yes                         | Yes (via Service)           | Yes                        | No                        |
| External Traffic     | Can expose (LoadBalancer)   | Primary purpose             | Primary purpose            | No direct effect          |
| Internal Traffic     | Primary purpose             | Can be used                 | Supports internal routing  | Primary purpose           |
| Flexibility          | Limited                     | Moderate                    | High                       | High                      |
| Multi-cluster        | No                          | Limited                     | Yes                        | No                        |
| Header-based Routing | No                          | Limited                     | Yes                        | N/A                       |
|----------------------|-----------------------------|-----------------------------|----------------------------|---------------------------|


## Examples 
