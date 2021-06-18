•	Reconfigure the existing deployment front-end:
Add a port specification named http exposing port 80/tcp of the existing container nginx add a selector entry with key foo and value bar 
•	Create a new service named front-end-svc exposing the container port http. Also use the new selector entry foo to select the service's target. 
•	Configure the new service to also expose the individual Pods via a port on the host on which they are scheduled. 





____WORKINPROGESS!!!!