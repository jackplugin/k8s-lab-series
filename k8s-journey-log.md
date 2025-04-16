# Record what I learned during the journey of learning kubernetes

## Set worker role for a node

```bash
# show cluster nodes
jack@LAPTOP-1ENIKL4J:~$ kubectl get node
NAME                 STATUS   ROLES           AGE     VERSION
multi-node-lab       Ready    control-plane   3d18h   v1.32.0
multi-node-lab-m02   Ready    <none>          3d18h   v1.32.0
multi-node-lab-m03   Ready    <none>          3d18h   v1.32.0

# update label for nodes
jack@LAPTOP-1ENIKL4J:~$ kubectl label node multi-node-lab-m02 node-role.kubernetes.io/worker=worker
node/multi-node-lab-m02 labeled
jack@LAPTOP-1ENIKL4J:~$ kubectl label node multi-node-lab-m03 node-role.kubernetes.io/worker=worker
node/multi-node-lab-m03 labeled

# show cluster nodes
jack@LAPTOP-1ENIKL4J:~$ kubectl get node
NAME                 STATUS   ROLES           AGE     VERSION
multi-node-lab       Ready    control-plane   3d18h   v1.32.0
multi-node-lab-m02   Ready    worker          3d18h   v1.32.0
multi-node-lab-m03   Ready    worker          3d18h   v1.32.0
```

## Standard DNS Naming Convention of Pod

```bash

<pod-ip-with-dashes>.<namespace>.pod.cluster.local

# for example, the IP of a pod in default namespace is 10.244.2.6, its dns name will be 10-244-2-6.default.pod.cluster.local
kubectl run -it --rm dns-test --image=busybox:1.28 --restart=Never -- nslookup 10-244-2-6.default.pod.cluster.local

# output
Server:    10.96.0.10
Address 1: 10.96.0.10 kube-dns.kube-system.svc.cluster.local

Name:      10-244-2-6.default.pod.cluster.local
Address 1: 10.244.2.6  
```
