```
To create a new SA:

$ kubectl create serviceaccount my-sa -n my-ns

Verification:
$ kubectl get sa -n my-ns

Verification:
$ kubectl create clusterrole new-cluster-role --verb=create,list --resource=daemonsets,deployments,replicaset,pods -n my-ns --dry-run -o yaml 

To create ClusterRole
$ kubectl create clusterrole new-cluster-role --verb=create,list --resource=daemonsets,deployments,replicaset,pods -n my-ns



Verification:
$ kubectl create clusterrolebinding new-cluster-role-binding --clusterrole=new-cluster-role --serviceaccount=default:my-sa  -n my-ns --dry-run -o yaml

To create ClusterRoleBinding
$  kubectl create clusterrolebinding new-cluster-role-binding --clusterrole=new-cluster-role --serviceaccount=default:my-sa -n my-ns
```