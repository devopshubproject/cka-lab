```
$ kubectl create -f pvc.yml

$ kubectl create -f pod.yml

$ kubectl delete pod my-nginx-pod --grace-period=0 --force

$ kubectl patch pvc pvc-q1 -p '{ "spec": { "resources": { "requests": { "storage": "70Mi" }}}}'

(or)

$ kubectl edit pvc.yaml

--> Update the storage size

$ kubectl create -f my-nginx.yaml
```