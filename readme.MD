# k8s volumes

***EBS, EFS both can be used for creating volumes in k8s.
there are two different methods for creating and managing persistent storage (volumes) for workloads.*** 

* static provisioning
* dynamic provisioning

**static provisioning:** 

storage resources are manually created and configured by an administrator. These resources, known as PersistentVolumes (PVs), are created in advance and are available for Kubernetes to use when a workload requests storage. This approach can be more controlled, but it requires additional manual work and ongoing management.

**How Static Provisioning Works**

* The administrator creates a PersistentVolume (PV) manually, specifying the details such as storage type (e.g., NFS, EBS, etc.), capacity, and access modes.
 
* Users then create a PersistentVolumeClaim (PVC), which requests a certain amount of storage.
Kubernetes will attempt to match the PVC with an available PV that meets the claim's requirements (e.g., capacity, access mode).
* Once matched, the PVC is bound to the PV, and the storage is available to the workload.

