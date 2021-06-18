1.	Create a new nginx Ingress resource as follows: 
o	Name: pong 
o	Namespace: ing-internal 
o	Exposing service hi on path /hi using service port 5678
o	Exposing service test on path /test using service port 5678  
o	The availability of service hi can be checked using the following command, which should return hi: 
o	curl -kL <INTERNAL_IP>/hi 
o	The availability of service test can be checked using the following command, which should return test 
o	curl -kL <INTERNAL_IP>/test 
