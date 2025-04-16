# Static PV Provisioning with hostPath in Multi-Node Kubernetes Cluster

## Preface

静态供给Persistence Volume指的是管理员提前手动创建Persistence Volume以供有存储需要的Pod通过Persistence Volume Claim的方式来取得存储卷并将其mount到容器内的目标目录. 目前有多种选项可以支持我们实现这种静态供给，比如hostpath, local volume, NFS etc, 本文主要聚焦于hostpath来进行实现以理解其背后的管理和控制机制.为了更好的实践和理解从PV创建，PVC声明到Pod通过PVC请求存储的整个过程，我们选用mysql做为存储请求方并分别为PV, PVC的创建和最终的POD部署开发了单独的manifest.

## Deployment Environment - multi-node minikube cluster

为理解在多节点集群环境下基于hostpath进行persistence volume静态供给的原理，文本采用3节点minikube cluster作为部署环境.

```bash
# show cluster nodes
jack@LAPTOP-1ENIKL4J:~$ kubectl get node
NAME                 STATUS   ROLES           AGE     VERSION
multi-node-lab       Ready    control-plane   3d18h   v1.32.0
multi-node-lab-m02   Ready    worker          3d18h   v1.32.0
multi-node-lab-m03   Ready    worker          3d18h   v1.32.0
```

## Manifest Files

- 01.static-hostpath-pv-for-mysql.yaml - persistence volume manifest
- 02.pvc-from-static-pv-for-mysql.yaml - persistence volume claim manifest
- 03.deployment-mysql-using-pvc.yaml   - pod deployment manifest

## Deploy & Check Status

```bash
# apply the manifest files
kubectl apply -f .

# check the status of pv
kubectl get pv | grep mysql

# check the status of pvc
kubectl get pvc | grep mysql

# check the status of pod
kubectl get pod | grep mysql
```

## What I learned during working with hostpath to statically provision persistence volume in a multi-node cluster

- Always specify `storageClassName` in pv and pvc manifest to achieve accurate matching. The specified `storageClassName `should not be conflict with the existing ones, customizing it. Without specifying `storageClassName`, the pvc will use default `storageClassName`, which may not be your intention. Avoding to use `storageClassName: ""`, it may lead to confustion.

- Always enforce `nodeAffinity `rules in pv or pod manifest to guarantee pod scheduling on the node providing volume. Without `nodeAffinity`, Kubernetes will dynamically select a node based on the cluster state at deployment time, which may not be the node you intended.

- When the path (e.g. `path: /data/mysql`) specified for `hostPath:` is not existing, k8s will automatically create it by default on the node.
