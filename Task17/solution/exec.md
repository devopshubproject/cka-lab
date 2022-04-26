```
$ kubectl get nodes -l name=node-01

$kubectl cordon node01

$ kubectl drain node01 --ignore-daemonsets=true --delete-local-data=true --force=true

```
