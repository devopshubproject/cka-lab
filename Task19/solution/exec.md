```
To create a new namespace

$ kubectl create ns tools

To create a pod on the created ns

$ kubectl run jenkins --image=jenkins --generator=run-pod/v1 -n tools
```