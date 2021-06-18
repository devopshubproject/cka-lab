```
$ kubectl get node | grep -w  Ready | wc -l

$ kubectl describe nodes | grep Taints | grep -I NoSchedule | wc -l

$ echo 2 > /path/to/node.txt
```


```
kubectl describe nodes | grep -i taint | grep -v :NoSchedule | wc -l > /path/to/node.txt
```