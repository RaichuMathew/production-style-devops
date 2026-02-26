# Kubernetes Persistent Volume – Nginx Deployment

## Objective

Deploy an Nginx web server backed by a PersistentVolume using a
manual StorageClass and hostPath volume.

---

## Components Created

1. PersistentVolume (pv-nautilus)
   - Capacity: 2Gi
   - Access Mode: ReadWriteOnce
   - StorageClass: manual
   - Volume Type: hostPath (/mnt/security)

2. PersistentVolumeClaim (pvc-nautilus)
   - Requests: 2Gi
   - Access Mode: ReadWriteOnce
   - StorageClass: manual

3. Pod (pod-nautilus)
   - Container: nginx:latest
   - Mount Path: /usr/share/nginx/html
   - Uses pvc-nautilus

4. Service (web-nautilus)
   - Type: NodePort
   - NodePort: 30008

---

## Why Persistent Volumes?

PersistentVolumes decouple storage lifecycle from Pod lifecycle.

Unlike emptyDir:
- Data survives container restarts
- Storage is managed independently
- Suitable for stateful workloads

---

## Deployment

kubectl apply -f pv-pvc-pod-service.yaml

Verify:

kubectl get pv
kubectl get pvc
kubectl get pods
kubectl get svc
