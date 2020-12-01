# **Logging and Monitoring**

Heapster was one of the original projects that enabled monitoring and analysis features for kubernetes. You will see a lot of reference online when you look for reference architectures on monitoring Kubernetes. However, Heapster is now Deprecated and a slimmed down version was formed known as the Metrics Server.

You can have one metrics server per kubernetes cluster, the metric server retrieves metrics from each of the kubernetes nodes and pods, aggregates them and stores them in memory. Note that the metric server is only an in memory monitoring solution and does not store the metrics on the desk and as a result you cannot see historical performance data. For that you must rely on one of the advanced monitoring solutions we talked about earlier So, how are the metrics generated for the PODs on these nodes? Kubernetes runs an agent on each node known as the kubelet, which is responsible for receiving instructions from the kubernetes API master server and running PODs on the nodes.

The kubelet also contains a subcomponent known as as cAdvisor or Container Advisor. cAdvisor is responsible for retrieving performance metrics from pods, and exposing them through the kubelet API to make the metrics available for the Metrics Server. 
If you are using minikube for your local cluster, *run the command minikube addons enable metrics-server*. For all other environments deploy the metrics server by cloning the metrics-server deployment files from the github repository. And then deploying the required components using the *kubectl create command*. This command deploys a set of pods, services and roles to enable metrics server to poll for performance metrics from the nodes in the cluster. Once deployed, give the metrics-server some time to collect and process data. Once processed, cluster performance can be viewed by running the command *kubectl top node*.



## **Logs :**
Once the pod is running, we can view the logs using the *kubectl logs command* and the pod name. Use the **`–f`** option to stream the logs live. Note that these logs are specific to the container running inside the pod  meaning, as we learned before, Kubernetes PODs can have multiple docker containers in them. If there are multiple containers within a pod, You must specify the name of the container explicitly in the command.

#### **Ex :-**   
		kubectl logs <pod name>
	  	kubectl logs <podName> <ContainerName>
		kubectl logs -<Options> <PodName> <ContainerName>