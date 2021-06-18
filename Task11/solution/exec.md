```
To upgrade the kubeadm:

$ apt-get update && \
  apt-get install -y --allow-change-held-packages kubeadm=1.21.x-00
$ kubeadm version
$ kubeadm upgrade plan
$ kubectl drain controlplane
$ sudo kubeadm upgrade plan
$ sudo kubeadm upgrade apply v1.21.1
$ kubectl uncordon controlpane 

To update kubelet:

$ apt-get update && \
 apt-get install -y --allow-change-held-packages kubelet=1.21.x-00
$ sudo systemctl daemon-reload
$ sudo systemctl restart kubelet
```