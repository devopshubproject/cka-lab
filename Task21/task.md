A Kubernetes worker node, labelled with name "node-01" is in state NotReady . Investigate why this is the case, and perform any appropriate steps to bring the node to a Ready state, ensuring that any changes are made permanent.

```
$ kubectl get nodes
$ ssh node-01
$ sudo -i
$ systemctl status kubelet
$ systemctl start kubelet
$ systemctl enable kubelet
```