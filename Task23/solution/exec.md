Kube Scheduler is deployed as Static pod

Path: ` $ cd /etc/kubernetes/manifests/

```
$ cd /etc/kubernetes/manifests/
$ ls

`
root@controlplane:/etc/kubernetes/manifests# ls
etcd.yaml  kube-apiserver.yaml  kube-controller-manager.yaml  kube-scheduler.yaml
`

$ cp kube-scheduler.yaml /root
$ cd /root
$ vi kube-scheduler.yaml

`

root@controlplane:~# cat kube-scheduler.yaml 
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    component: kube-scheduler
    tier: control-plane
  name: custom-scheduler                                                        ### Change the name
  namespace: kube-system
spec:
  containers:
  - command:
    - kube-scheduler
    - --authentication-kubeconfig=/etc/kubernetes/scheduler.conf
    - --authorization-kubeconfig=/etc/kubernetes/scheduler.conf
    - --bind-address=127.0.0.1
    - --kubeconfig=/etc/kubernetes/scheduler.conf
    - --leader-elect=false                                                      ### Change the elect leader option from True to False to make it act as second scheduler
     - --scheduler-name=custom-scheduler                                        ### Add the new custom scheduler name  
    - --port=0
    image: k8s.gcr.io/kube-scheduler:v1.20.0
    imagePullPolicy: IfNotPresent
    ports:
    - contianerPort: 10263                                                      ### Change the default container port
    livenessProbe:
      failureThreshold: 8
      httpGet:
        host: 127.0.0.1
        path: /healthz
        port: 10263                                                             ### Change the liveness probe port to listen to new container port
        scheme: HTTPS
      initialDelaySeconds: 10
      periodSeconds: 10
      timeoutSeconds: 15
    name: kube-scheduler
    resources:
      requests:
        cpu: 100m
    startupProbe:
      failureThreshold: 24
      httpGet:
        host: 127.0.0.1
        path: /healthz
        port: 10263                                                             ### Change the startup probe port to listen to new container port   
        scheme: HTTPS
      initialDelaySeconds: 10
      periodSeconds: 10
      timeoutSeconds: 15
    volumeMounts:
    - mountPath: /etc/kubernetes/scheduler.conf
      name: kubeconfig
      readOnly: true
  hostNetwork: true
  priorityClassName: system-node-critical
  volumes:
  - hostPath:
      path: /etc/kubernetes/scheduler.conf
      type: FileOrCreate
    name: kubeconfig
status: {}
`

To check the un-used port

` netstat -tulpna | grep 10253 `

To apply the edited kube-scheduler.yaml

`$ kubectl create -f kube-scheduler.yaml`

To cross the provisioned custom scheduler

`$ kubectl get pods -n kube-system | grep scheduler`

Create and schedule a pod on new new custom scheduler

`$ kubectl create -f nginx.pod`

To cross check
` $ kubectl describe pod nginx`