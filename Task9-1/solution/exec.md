```
kubectl run nginx-app --image=nginx:1.11-alpine --replicas=3

kubectl set image deployment/nginx-app nginx-app=nginx:1.13.0-alpine --record=true

kubectl rollout undo deployment/nginx-app

kubectl rollout status -w deployment nginx-app 

kubectl rollout history deployment/nginx-app
```