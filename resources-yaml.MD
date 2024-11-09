**PV resouce yaml**
```
apiVersion: v1
kind: PersistentVolume
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","kind":"PersistentVolume","metadata":{"annotations":{},"name":"ebs-static-pv"},"spec":{"accessModes":["ReadWriteOnce"],"capacity":{"storage":"5Gi"},"csi":{"driver":"ebs.csi.aws.com","fsType":"ext4","volumeHandle":"vol-0bbc28d30247349f7"}}}
    pv.kubernetes.io/bound-by-controller: "yes"
  creationTimestamp: "2024-11-09T11:00:41Z"
  finalizers:
  - kubernetes.io/pv-protection
  - external-attacher/ebs-csi-aws-com
  name: ebs-static-pv
  resourceVersion: "77613"
  uid: 7443ed13-a40e-4e79-a9aa-3ecda88b5712
spec:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 5Gi
  claimRef:
    apiVersion: v1
    kind: PersistentVolumeClaim
    name: ebs-static-pvc
    namespace: default
    resourceVersion: "77596"
    uid: 5d2ceb7b-3cde-42b6-b612-9b5c5dc12dba
  csi:
    driver: ebs.csi.aws.com
    fsType: ext4
    volumeHandle: vol-0bbc28d30247349f7
  persistentVolumeReclaimPolicy: Retain
  volumeMode: Filesystem
status:
  lastPhaseTransitionTime: "2024-11-09T11:00:41Z"
  phase: Bound
```

**PVC resouce yaml**

```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"v1","kind":"PersistentVolumeClaim","metadata":{"annotations":{},"name":"ebs-static-pvc","namespace":"default"},"spec":{"accessModes":["ReadWriteOnce"],"resources":{"requests":{"storage":"3Gi"}},"storageClassName":"","volumeName":"ebs-static-pv"}}
    pv.kubernetes.io/bind-completed: "yes"
  creationTimestamp: "2024-11-09T11:00:41Z"
  finalizers:
  - kubernetes.io/pvc-protection
  name: ebs-static-pvc
  namespace: default
  resourceVersion: "77600"
  uid: 5d2ceb7b-3cde-42b6-b612-9b5c5dc12dba
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi
  storageClassName: ""
  volumeMode: Filesystem
  volumeName: ebs-static-pv
status:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 5Gi
  phase: Bound
```