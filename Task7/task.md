Add a side car container to the running pod logging-pod with the blow specification. 
The image of the sidecar container is busybox and the container writes the logs as below tail -n+1 /var/log/k8slog/application.log 
The container shares the volume logs with the application container the mounts to the directory /var/log/k8slog 
Do not alter the application container and verify the logs are written properly to the file 

looging-pod primary container logger does not write to any volumes, you need to create a volume from empty dir and mount it appropriately. 




____WORKINPROGESS!!!!