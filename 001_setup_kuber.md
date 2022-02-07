## Setup kubernetes
#
##### Play with Kubernetes
A simple, interactive and fun playground to learn Kubernetes
```
https://labs.play-with-k8s.com/
```
Add the desired number of servers. For example, 3 (1 master and 2 workers)
Commands example (paste your ips)

1. Initializes cluster master node:
```
 kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
```
2. Initialize cluster networking (on master):
```
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```
3. Join workers to cluster. (run for each worker)
```
 kubeadm join 192.168.0.13:6443 --token xeusvp.knyf1r0tk33669gf \
    --discovery-token-ca-cert-hash sha256:79e4b937a68c40fcc41fd1988c565a67d3e4fdf1735bfe3341f46026ff16d8fc
```
Check cluster nodes (on master):
```
kubectl get nodes
```