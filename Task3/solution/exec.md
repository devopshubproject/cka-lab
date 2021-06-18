```
kubectl top pods -l name=cpu-burner -n kube-system --no-headers=true | head -n 1 | awk '(print $1)' > /tmp/cpu.txt

(or)

kubectl top pods -l name=cpu-burner -n kube-system 

echo '<podname>' >> /tmp/cpu.txt
```