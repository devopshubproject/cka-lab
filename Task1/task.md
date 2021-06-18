*Create a PVC my-pvc with the capacity 10Gi and storage class k8s-csi-plugin. *

•	Assign the PVC to the pod named nginx-pod with image nginx and mount to path /usr/share/html
•	Ensure the pod claims the volume as ReadWriteMany access mode 
•	Use kubectl patch or kubectl edit to update the capacity of the PVC as 70Gi to record the change.
