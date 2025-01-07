

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

## Control and Management

- **Controller**: A control loop that watches the shared state of the cluster and makes changes to move the current state towards the desired state.

- **Operator**: A method of packaging, deploying, and managing a Kubernetes application using custom resources and controllers.

- **Kubectl**: The command-line tool for interacting with the Kubernetes API.

- **Kubeconfig**: A file used to configure access to Kubernetes clusters.

Understanding these terms will provide a solid foundation for working with Kubernetes and communicating effectively about its components and operations.

