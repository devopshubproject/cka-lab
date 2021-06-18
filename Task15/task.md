Set configuration context $ kubectl config use-context k8s Scale the deployment webserver to 6 pods


```
$ kubectl scale deployment/webserver --replicas=6
```



Name: non-persistent-redis
Container image: redis
Named-volume with name: cache-control
Mount path: /data/redis
It should launch in the pre-prod namespace and the volume MUST NOT be persistent.


```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: non-persistent-redis
  name: non-persistent-redis
spec:
  volumes:
  - name: cache-control
    emptyDir: {}
  containers:
  - image: redis
    imagePullPolicy: IfNotPresent
    name: non-persistent-redis
    resources: {}
    volumeMounts:
    - mountPath: /data/redis
      name: cache-control
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```


From the Pod label name:cpu-utilizer, find pods running high CPU workloads and write the name of the Pod consuming most CPU to the file /opt/cpu.txt (which already exists)


```
$ kubectl top pods -l name=cpu-utilizer -n kube-system

$ kubectl top pods -l name=cpu-utilizer -n kube-system --no-headers | head -n 1 | --sort.by=  >> /opt/cpu.txt
```