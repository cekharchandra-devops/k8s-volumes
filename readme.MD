# k8s volumes

In EKS, by default, the in-tree Kubernetes storage plugin is used to provision gp2 (General Purpose SSD) EBS volumes for persistent storage
```
in-tree Kubernetes storage plugin is a legacy storage solution integrated directly into the Kubernetes core
```
So whenever you create a PersistentVolumeClaim (PVC) in EKS without specifying a StorageClass explicitly, it makes use of the gp2 default storage class that is part of in-tree Kubernetes storage plugin.

This means that the in-tree AWS plugin for storage, including logic to provision gp2 volumes, was tightly coupled with Kubernetes and managed by the same cloud controller manager responsible for other AWS-related tasks like node management.

**Deprecation of the in-tree storage plugin**

* With the deprecation of the in-tree storage plugin and the shift to the EBS CSI driver, EKS clusters now use the CSI driver to provision EBS volumes.

* This transition provides greater flexibility, allowing you to define custom volume types through StorageClass configurations giving you more control over storage performance and cost.

**Container Storage Interface (CSI)**

* CSI provides a standardized framework for storage vendors (like AWS, GCP, Azure etc) to integrate their storage solutions with Kubernetes.

* It defines the APIs and protocols that any storage system must implement to interact with Kubernetes.

* The EBS CSI driver uses this framework to allow Kubernetes to create, attach, mount, and delete EBS volumes for pods running in a cluster.

* Unlike in-tree storage plugins, that were built directly into Kubernetes's core, EBS CSI driver is developed independently of Kubernetes, making it easier to update, troubleshoot, and improve


there are two different methods for creating and managing persistent storage (volumes) for workloads.*** 

* static provisioning
* dynamic provisioning

**static provisioning:** 

storage resources are manually created and configured by an administrator. These resources, known as PersistentVolumes (PVs), are created in advance and are available for Kubernetes to use when a workload requests storage. This approach can be more controlled, but it requires additional manual work and ongoing management.

**Steps to create and cliam volume in K8s**

* Create an EBS volume with the required storage limit in the same availability zone as the worker node where the pod will cliam this volume.

* install ebs csi driver to intergrate ebs volumes with kubenetes

* add permissions to worker node's IAM Role to access volumes from k8s cluster

* create PV, PVC resources to represent ebs volume inside the cluster and request the volume 

* mount the volume in the required pods.



