# Kubernetes Deployments

A Deployment contains (usually) one Application aka Pod you want to host.

## Deployment to Application Relationship

In general, there should be a 1:1 relationship between a Deployment and an application or microservice, as this provides several benefits:

1. **Separation of Concerns:** Each deployment manages a single application or service, making it easier to understand, update, manage, and troubleshoot.
2. **Independent Scaling:** Different parts of your system can be scaled independently based on their specific needs.
3. **Targeted Updates:** You can update one part of your system without affecting others.
4. **Resource Management:** It's easier to allocate and manage resources for each component separately.
5. **Simplified Monitoring:** Each deployment can have its own set of metrics and logs, making it easier to monitor and debug.

### Examples of 1:1 Deployment to Application Relationship

Web Application:

- Frontend Deployment
- Backend API Deployment
- Database StatefulSet

Microservices Architecture:

- User Service Deployment
- Order Service Deployment
- Payment Service Deployment
- Notification Service Deployment



## Components of a Kubernetes Deployment

A Kubernetes Deployment can include several key components and configurations:

1. **Metadata**:
   - Name: Unique identifier for the Deployment
   - Namespace: The namespace where the Deployment will be created
   - Labels: Key-value pairs for organizing and selecting API objects

2. **Spec**:
   - Replicas: Number of desired pod replicas
   - Selector: Label selector for pod templates
   - Template: Pod template specification
     - Metadata: Labels for the pods
     - Spec: Container specifications

3. **Container Specifications**:
   - Image: Docker image to use for the container
   - Name: Name of the container
   - Ports: List of ports to expose from the container
   - Environment variables: Key-value pairs for environment configuration
   - Resource requests and limits: CPU and memory specifications
   - Volume mounts: Attachment points for volumes in the container

4. **Update Strategy**:
   - Type: RollingUpdate (default) or Recreate
   - MaxUnavailable: Maximum number of pods that can be unavailable during the update
   - MaxSurge: Maximum number of pods that can be created over the desired number of pods

5. **Volumes**:
   - Definition of volumes that can be mounted by containers

6. **Pod Disruption Budget**:
   - Specification for the number of pods that must be available during voluntary disruptions

7. **Affinity and Anti-Affinity Rules**:
   - Node affinity/anti-affinity
   - Pod affinity/anti-affinity

8. **Tolerations**:
   - Specifications for which taints the pods can tolerate

9. **Security Context**:
   - Security settings for pods or containers

10. **Liveness, Readiness, and Startup Probes**:
    - Definitions for health checks and startup behavior





## Workload Resources

- **StatefulSet**: Manages stateful applications, providing guarantees about the ordering and uniqueness of pods.

- **DaemonSet**: Ensures that all (or some) nodes run a copy of a pod, typically for node-level operations.

- **Job**: Creates one or more pods and ensures that a specified number of them successfully terminate.

- **CronJob**: Manages time-based Jobs, for example, to schedule a Job execution periodically.

## Service and Networking

- **Service**: An abstract way to expose an application running on a set of Pods as a network service.

- **Ingress**: Manages external access to services in a cluster, typically HTTP.

- **NetworkPolicy**: A specification of how groups of pods are allowed to communicate with each other and other network endpoints.

## Configuration and Storage

- **ConfigMap**: An API object used to store non-confidential data in key-value pairs.

- **Secret**: Similar to ConfigMap but for confidential data, stored in base64 encoding.

- **Volume**: A directory containing data, accessible to the containers in a pod.

- **PersistentVolume (PV)**: A piece of storage in the cluster provisioned by an administrator or dynamically.

- **PersistentVolumeClaim (PVC)**: A request for storage by a user, which can be fulfilled by a PV.

## Metadata and Organization

- **Namespace**: A way to divide cluster resources between multiple users, teams, or projects.

- **Label**: Key-value pairs attached to objects for identification and organization.

- **Annotation**: Similar to labels, but for non-identifying metadata.









# Defining a Pod




#### Why have multiple containers in one Pod?

Multi-container Pods are designed to support co-located, co-managed helper processes for a primary application. These containers work together in a tightly coupled manner to provide a unified service.

### Use Cases for Multi-Container Pods:

1. **Sidecar Pattern**: 
   A sidecar container extends and enhances the main container.
   Example: Log watchers, monitoring agents, or data sync services.

2. **Ambassador Pattern**: 
   An ambassador container proxies network traffic to/from the main container.
   Example: Handling SSL termination or connecting to a sharded database.

3. **Adapter Pattern**: 
   An adapter container standardizes and normalizes output from the main container.
   Example: Transforming application logs into a specific format.

4. **Init Containers**: 
   Containers that run and complete before the app containers start.
   Example: Setting up volumes, performing database migrations, or delaying app startup until dependencies are available.

5. **Service Mesh Sidecar**: 
   In service mesh architectures, a sidecar container handles inter-service communication.
   Example: Istio's Envoy proxy sidecar.

6. **Shared File System**: 
   Containers that need to share a file system.
   Example: A content management system where one container serves files and another processes uploads.

7. **Co-located Processes**: 
   Tightly coupled processes that need to communicate via IPC mechanisms.
   Example: A main application and a helper process communicating via a local Unix socket.

### Key Benefits:

- Shared resources and namespace
- Simplified communication between containers
- Co-located and co-scheduled processes
- Unified lifecycle management

