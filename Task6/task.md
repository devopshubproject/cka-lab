Create a NetworkPolicy named k8s-netpol in the namespace namespace-netpol in a way that pods running on namespace internal on port 9200 can only access pods running in namespace-netpol.
a. Allow the pods to communicate if they are running on port 9200 within the namespace
b. Ensure the NetworkPolicy doesn’t allow other pods that are running other than port 9200 
c. The communication from and to the pods running on port 9200
d. No pods running on port 9200 from other name spaces to allowed 

NB: There will be a default deny all from any namespace netpol will be already present.




____WORKINPROGESS!!!!