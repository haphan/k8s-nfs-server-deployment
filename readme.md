## NFS ReadWriteMany Volume in kubernetes 

Solving the use-case of rwx in k8s where deploying a full-blown glusterfs is undesirable.

Adapting from the [nfs example of kubernetes](https://github.com/kubernetes/examples/tree/master/staging/volumes/nfs) 

`If you think read-write many volume is cool, think again.`

### Kubernetes host node requirements

- `nfs-common` (contains `mount.nfs`)
- nfs kernel modules (`modprobe nfs`)

### Deploy self-hosted nfs-server

```bash
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
``` 

### Deploy nginx to consume rwx volume

```bash
kubectl apply -f pv-nfs.yaml
kubectl apply -f nginx.yaml
```