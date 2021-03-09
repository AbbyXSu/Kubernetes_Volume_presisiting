# Kubernetes_Volume_presisiting

## Storage Requirements for Volume 
- The storage does not depend on the pod lifecycle 
- Storage must be accessible for all nodes, it shoyuld not be in any namespaces
- storage need to survice even cluster crashes

## User case
- Database
- pre-existing files for writes and reads

Presistent Volume is a cluster resource that is used to store data, it is created via YAML file with kind as PersistentVolume and spec defined capacity - storage and volumeMode etc.

## Where it is stored ?

It could be cloud-storage, nfs server ot local disk, however, it should be noted that storage acts as external pugin to the cluster, it is created, managed, backup and monitored by the K8s Adminstrator and K8s only responsibile of the persistent Volume in the K8s Cluster, not the storage. 

K8s users then explicitly configure the application Yaml to use the persistent volume compoenent, therefore the yaml file claim the persistent volume (PVC) that matched the yaml requirements, and use the persistent volume (PV) taht connected to the actual storage backend.

persistent volume claim has to exist in the same namespace as the pod using the claim, when presistent volume would be left outside the namespace

# Statefulset for stateful application 
Stateful application are applications that persists data, such as databases, MYSQL or Elastict search etc. It is deployed using StatefulSet

Stateless applications do not keep record of the state and each request is completely new without any footprint.it is deployed using Deployment

