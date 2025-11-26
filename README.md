
## Nextcloud on Kubernetes

This repo contains the Kubernetes manifests needed to run Nextcloud and MariaDB.
Persistent data is stored on an NFS server. **Passwords have been changed of course**.

**Storage**

Make sure these folders exist on your NFS server:

nextcloud_app

nextcloud_db

The NFS path used by the cluster is:
```bash
192.168.88.21:/export/k8s-nfs/
```
## Deploy

Apply everything in order:

```bash
kubectl create namespace nextcloud

kubectl apply -f pvc.yaml -n nextcloud

kubectl apply -f LoadBalancer.yaml -n nextcloud

kubectl apply -f Secrets.yaml -n nextcloud

kubectl apply -f MariaDB_Deployment.yaml -n nextcloud

kubectl apply -f Nextcloud_Deployment.yaml -n nextcloud
```

