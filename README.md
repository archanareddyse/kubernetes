# kubernetes
kubernetes by minicube
Minikube is a tool that allows you to run a single-node Kubernetes cluster inside a virtual machine, on your own computer.
Run the installer to complete the installation process
Set the path for minikube in the Environment variables
Start your cluster by running the following command in powershell
	> minikube start             [Docker service should be running]
To check which ip address minikube is running type
	> minikube ip
Then type  kubectl get po –A to see the nodes
Create a sample deployment and expose it on port 8080:.
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4 
Create a sample deployment and expose it on port 8080:.
kubectl expose deployment hello-minikube --type=NodePort --port=8080
Use kubectl to forward the port to any other port 
	 kubectl port-forward service/hello-minikube 7080:8080
Check your application on the browser at the port 7080
	in browser open http://localhost:7080/
Create a new app using Node.js and Mongodb for creating and updating user profile.
Steps : Create the required configuration files 
	mongo-config.yaml
	mongo-secret.yaml
	mongo.yaml
	webapp.yaml
Mongo-config.yaml		apiVersion: v1 
				kind: ConfigMap 
				metadata: 
		    			  name: mongo-config 
				data: 
		           		               mongo-url: mongo-service
Run all the configuration files
	> kubectl apply –f  mongo-config.yaml
Check the services running using the command:	
	kubectl get services
Use kubectl to forward the port:	
	kubectl port-forward service/webapp-service 6080:8080
now ckeck in localhost in 6080
