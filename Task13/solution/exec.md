```
To list the nodes
$ kubectl get node

To ssh into the node
$ ssh k8s-node

Change to sudo
$ sudo -i

# Check the status of the kubelet
$ systemctl status kubelet 

# Start the kubelet
$ systemctl start kubelet

Enable the kubelet to make it permanent
$ systemctl enable kubelet
```