Container/Cluster/Pod/Node : https://medium.com/faun/understanding-nodes-pods-containers-and-clusters-778dbd56ade8

KUBERNETES :- The purpose of Kubernetes is to host your applications in the form of containers in an automated fashion
			  so that you can easily deploy as many instances of your application as required and easily enable communication
			  between different services within your application.
			  
			  The Kubernetes cluster consists of a set of nodes which may be physical or virtual, on-premise or
			  on cloud that host applications in the form of containers.

MASTER NODE : The master node is responsible for managing the Kubernetes cluster. Storing information regarding the different nodes 
			  planning which containers goes where, monitoring the nodes and containers on them etc. 
			  The Master node does all of these using a set of components together known as the control plane components.
			  
	--> ETCD Cluster : stores info about cluster. Etcd is a database that stores information in a key-value format.
					   When you run ETCD it starts a service that listens on Port 2379 by default. The ETCD datastore stores information 
					   regarding the cluster such as the nodes, pods, configs, secrets, accounts, roles, bindings and others.
					   Every information you see when you run the kubectl get command is from the ETCD server. Every change you make to your cluster, 
					   such as adding additional nodes, deploying pods or replica sets are updated in the ETCD server. 
					   Only once it is updated in the ETCD server, is the change considered to be complete.
					   
					   --advertise client-urls https://${INTERNAl_IP}:2379 :- This is the address on which ETCD listens. 
								It happens to be on the IP of the server and on port 2379, which is the default port on which etcd listens. 
								This is the URL that should be configured on the kube-api server when it tries to reach the etcd server.
								If you setup your cluster using kubeadm then kubeadm deploys the ETCD server for you as a POD in 
								the kube-system namespace. 
	
	--> Kube API : Responsible for Orchestration of services.
					The kube-apiserver is at the center of all the different tasks that needs to be performed to make a change in the cluster.
					To summarize, the kube-api server is responsible for Authenticating and validating requests, retrieving and 
					updating data in ETCD data store, in fact, kube-api server is the only component that interacts directly with the etcd datastore.
					The other components such as the scheduler, kube-controller-manager & kubelet uses the API server 
					to perform updates in the cluster in their respective areas.
	
	--> kube Scheduler : Responsible for Scheduling applications or containers or nodes.
						 A scheduler identifies the right node to place a container based on the containers, Resource requirements, 
						 the worker nodes capacity or any other policies or constraints such as tents and tolerations or node affinity rules 
						 that are on them.


	--> Controller Manager : controllers take care of diffrent functions.
									A controller is a process that continuously monitors the state of various components within the system 
								and works towards bringing the whole system to the desired functioning state.
								For example the node controller is responsible for monitoring the status of the nodes and taking necessary
								actions to keep the application running. It does that through the kube-api server. 
								The node controller checks the status of the nodes every 5 seconds. That way the node controller 
								can monitor the health of the nodes, if it stops receiving heartbeat from a node, 
								the node is marked as unreachable but it waits for 40 seconds before marking it unreachable, 
								after a node is marked unreachable it gives it five minutes to come back up if it doesn’t, it removes the
								PODs assigned to that node and provisions them on the healthy ones. 
								
									If the PODs are part of a replica set the next controller is the replication controller.
								It is responsible for monitoring the status of replica sets and ensuring that the desired number of
								PODs are available at all times within the set. If a pod dies it creates another one.
								Now those were just two examples of controllers.
										
									There are many more such controllers available within kubernetes. Now how do you see these 
								controllers and where are they located in your cluster. They're all packaged into a single process 
								known as kubernetes controller manager. When you install the kubernetes controller manager 
								the different controllers get installed as well.
	
WORKER NODES :
	--> Kubelet : Listens instructions from kubeAPI server and manages containers.
					A kubelet is an agent that runs on each node in a cluster. It listens for instructions from the kube-api server and 
					deploys or destroys containers on the nodes as required. The kube-api server periodically fetches status reports from the 
					kubelet to monitor the state of nodes and containers on them.
					
						The kubelet in the kubernetes worker node, registers the node with the kubernetes cluster. When it receives 
					instructions to load a container or a POD on the node, it requests the container run time engine, which may be Docker, 
					to pull the required image and run an instance. The kubelet then continues to monitor the state of the POD 
					and the containers in it and reports to the kube-api server on a timely basis.
					
						If you use kubeadm tool to deploy your cluster, it does not automatically deploy the kubelet.
					Now that's the difference from the other components. You must always manually install the kubelet on your worker nodes. 
					Download the installer, extract it and run it as a service.
					
	--> Kube-Proxy : Communication between worker nodes are enabled by component that runs on the worker node known as the Kube-proxy service. 
					 The Kube-proxy service ensures that the necessary rules are in place on the worker nodes to allow the 
					 containers running on them to reach each other.
					 

Commands :
	--> How to create pods :- kubectl run nginx --image nginx
								It first creates a POD automatically and deploys an instance of the nginx docker image.
								In this case the nginx image, is downloaded from the docker hub repository.
		
	--> How do we see the list of PODs available? :- kubectl get pods
	
	--> kubectl get pods -o wide : for long details
	--> kubectl describe pod <podname> : ultra long details of the pod
	--> 

Creating a pod using YAML file. 

Pod-Definition.yml
	apiversion: v1
	kind: pod
	metadata:
		name: myapp-pod
		labels:
			app: myapp
	specs:
		containers:
			- name: nginx 
			  image:nginx
-> To launch pod using yaml file:- kubectl create -f <filename>.yml 
-> To apply changes when we edited the file :- kubectl apply -f <filename>.yml
-> Automatically applies changes after edit :- kubectl edit pod <podname>
-> creates a yaml file without launching a pod :- kubectl run <name> --image=<imageName> --dry-run=client -o yaml > <filename>.yml

Creates a Replication controller :-

rc-Definition.yml
	apiversion: v1
	kind: ReplicationController
	metadata:
		name: myapp-rc
		labels:
			app: myapp
			type: front-end
	specs:
	- template:
		metadata:
			name: myapp-pod
			labels:
				app: myapp
		specs:
			containers:
			- name: nginx 
			  image:nginx	
	replicas:3

-> To launch replication controller :- kubectl create -f <filename>.yml 

Creates Replica Set :-

replicaset-definition.yml

apiversion: apps/v1
	kind: Replicaset
	metadata:
		name: myapp-replicaset
		labels:
			app: myapp
			type: front-end
	specs:
	- template:
		metadata:
			name: myapp-pod
			labels:
				app: myapp
		specs:
			containers:
			- name: nginx 
			  image: nginx	
	replicas:3
	selector:
		matchLabels:
			type: front-end

-> To launch replicationset :- kubectl create -f <filename>.yml
-> To increase no of replicas :- 
		Increase by updating the file replicaset definition file:- kubectl replace -f <filename>.yml
		Increase from commandline :- kubectl scale --replicas=6 -f <filename>.yml
		NOTE :- using scale command with filename does increase the replicas but doesnt increase in replicaset-definition file.
		Increase from commandline :- kubectl scale --replicas=6 replicaset <Name specified in replicaset definition file>
-> To get brief details :- kubectl explain <resource name>

--> we can set alias for commands using alias command :- alias <shortcut>='<actual command>'

--> To see all the created objects at once :- kubectl get all


NameSpaces :-
	--> To view pods in other namespace :- kubectl get pods --namespace=<namespace name>
	--> To create objects in other namespaces :- kubectl create -f <filename> --namespace=<nameSpaceName>
	--> To create namespace from yaml file :- kubectl create -f <filename>
	--> To create namespace :- kubectl create namespace <nameSpaceName>
	--> To change in to the namespace :- kubectl config set-context $(kubectl config current-context) --namespace=<nameSpaceName>
	--> To get pods in all namespaces :- kubectl get pods --all-namespaces
	--> To connect to database in own namespace :- kubectl connect db-service
	--> To connect to database in other namespace :- kubectl connect db-service.<nameSpaceName>.svc.cluster.local
	
NOTE :- You can set resource quota by creating resource quota yaml file

Example file of resourcequota.yml
version: v1
kind: Resourcequota
metadata:
	name: compute-quota
	namespace: Dev
specs:
	hard:
		pods: "10"
		request.cpu: "4"
		request.memory: 5Gi
		limit.cpu: "10"
		limit.memory: 10Gi


Services: 
		Services enable communication between various components within and outside of the application. 
		Kubernetes services helps us connect applications together with other applications or users.
		
		The kubernetes service is an object just like PODs, Replicasetor and Deployments. One of its use case is to listen to a port on the Node 
		and forward requests on that port to a port on the POD running the web application. This type of service is known as a NodePortservice 
		because the service listens to a port on the Node and forwards requests to PODs.

		There are other kinds of services available.
		-> The first one is NodePort :
			NodePort where the service makes an internal POD accessible on a Port on the Node.
			That is because NodePorts can only be in a valid range which by default is from 30000 to 32767.
		
		-> The second is cluster IP.
			And in this case the service creates a virtual IP inside the cluster to enable communication between different services such 
			as a set of front end servers to a set of back end servers.
		
		-> The third type is a LoadBalancer : 
			where it provisions a load balancer for our service in supported cloud providers. A good example of that would be to distribute 
			load across the different web servers in your front end tier.

Example file of nodeport service services.yml

apiVersion: v1
kind: Service
metadata:
	name: myapp-service
spec:
	type: NodePort
	ports:
	-	targetPort: 80
		port: 80
		nodePort: 30008
	selctor:
		app: myapp
		type: front-end
		
--> To get all services with running in system :- kubectl get services.

Example file of clusterIP service services.yml

apiVersion: v1
kind: Service
metadata:
	name: back-end
spec:
	type: ClusterIP
	ports:
	-	targetPort: 80
		port: 80
	selctor:
		app: myapp
		type: back-end

NOTE: If you dont specify the type by default it takes ClusterIP.


--> To change the image of runnnig deployment :- kubectl set image deployment nginx nginx=nginx:1.18
-->  :- kubectl expose deployment nginx --port 80