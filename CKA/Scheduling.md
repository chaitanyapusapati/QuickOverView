## **Manual Scheduling :**
How exactly does a scheduler work in the backend. Let's start with a simple pod definition file. Every POD has a field called NodeName that, by default, is not set. You don’t typically specify this field when you create the manifest file, 
Kubernetes adds it automtically.The scheduler goes through all the pods and looks for those that do not have this property set.
Those are the candidates for scheduling. 

It then identifies the right node for the POD, by running the scheduling algorithm. Once identified it schedules the POD on the Node by setting the node Name property to the name of the node by creating a bindingobject. So if there is no scheduler to monitor and schedule nodes what happens? The pods continue to bein a pending state. So what can you do about it. You can manually assign pods to node yourself. Well without a scheduler, the easiest way to schedule a pod is to simply set the node name field to the name of the node in your pod specification while creating the POD. The pod then gets assigned to the specified node. You can only specify the node name at creation time.

What if the pod is already created and you want to assign the pod to a node? Kubernetes won’t allow you to modify the node Name property of a pod. So another way to assign a note to an existing pod is to create a bindingobject and send a post request to the pod binding API thus mimicking what the actual scheduler does. In the bindingobject you specify a target node with the name of the node. Then send a post request to the pods binding API with the data set to the binding object in a JSON format. So you must convert the YAML file into its equivalent JSON format.

**Example file of Binding object Pod-bind-definition.yml**
```yaml
apiVersion: v1
kind: Binding
metadata:
  name: nginx
target:
  apiVersion: v1
  kind: Node
  name: node02
```
	
## **Labels and Selectors :**
How are labels and selectors used in Kubernetes? We have created a lot of different types of Objects in Kuberentes. Pods, Services, ReplicaSets and Deployments. etc. For Kubernetes, all of these are different objects. Over time you may end up having hundreds or thousands of these objects in your cluster. Then you will need a way to filter and view different objects by different categories such as to group objects by their type or view objects by application or by their functionality whatever it may be. You can group and select objects using labels and selectors for each object attach labels as per your needs, like app, function etc.

Then while selecting specify a condition to filter specific objects. For example app == App1. So how exactly do you specify labels in kubernetes. In a pod-definition file, under metadata, create a section called labels. Under that add the labels in a key value format. You can add as many labels as you like. Once the pod is created, to select the pod with the labels use the	kubectl get pods command along with the selector option, and specify the condition like app=App1. Now this is one use case of labels and selectors.

Kubernetes objects use labels and selectors internally to connect different objects together. For example to create a replicaset consisting of 3 different pods, we first label the pod definition and use selector in a replicaset to group the pods in the replica-set set definition file.

**Example of using selector :** 
```
kubectl get all --selector env=prod,bu=finance,tier=frontend
```

## **Taints and Tolerations :**
Tains and Toleration have nothing to do with security or intrusion on the Cluster. Taints and toleration are used to set 
restrictions on what Nodes pods can be scheduled.
		
On a Node let us start with a simple cluster with three worker nodes, the nodes are named `one`, `two` and `three`. We also have a set of pods that are to be deployed on these nodes. Let's call them `A B C` and `D`.  Now let us assume that we have dedicated resources on `Node 1` for a particular use case or application so we would like only those pods that belong to this  application to be placed on Node 1. First we prevent all pods from being placed on the Node by placing a taint on the Node. Pods have no toleration which means unless specified otherwise none of the pods can tolerate any taint. So in this case none of the pods can be placed on `Node 1` as none of them can tolerate the taint. this solves half of our requirement no unwanted pods are going to be placed on this node. The other half is to enable certain pods to be placed on this node. For this we must specify which pods are tolerant to this particular attempt. In our case we would like to allow only `Pod D` to be placed on this node so we add a toleration to `Pod D`. `Pod D` is now tolerant to taint so when thes cheduler tries to place this pod on `Node 1` it goes through. `Node 1` can now only accept pods that can tolerate the taint.

**Example of Taint :** 
```
kubectl taint nodes <nodeName> key=value:taint-efect
```
**NOTE :** taint-efect can be NoSchedule Or PreferNoSchedule or NoExecute
				
**Example of tolerations in pod file Pod-Definition.yml**
```yaml
apiVersion:
kind: pod
metadata:
	name: myapp-pod
spec:
  containers:
  -	name: nginx-container
	image: nginx
  tolerations:
  -	key: "app"
	operator: "Equal"
	value: "blue"
	effect: "NoSchedule"
```
**Note :** Taints are applied on nodes and Tolerations are applied to pods.



## **NodeSelctors :** 
Let us start with a simple example.
You have a three node cluster of which two are smaller nodes with lower hardware resources and one of them is a larger node configured with higher resources you have different kinds of workloads running in your cluster. You would like to dedicate the data processing workloads that require higher horsepower to the larger node as that is the only node that will not run out of resources in case the job demands extra resources.

However, in the current default setup, any pods can go to any nodes. So Pod C in this case may very well end up on nodes two or three which is not desired. To solve this we can set a limitation on the pods so that they only run on particular nodes.
There are two ways to do this. The first is using Node selectors which is the simple and easier method.

**Example file of pod with nodeSelector :**
```yaml
apiVersion:
kind: pod
metadata:
  name: myapp-pod
spec:
  containers:
  -	name: data-processor
	image: data-processor
  nodeSelector:
	size: Large
```
**Note :** prior creating pods with nodeSelector rules in definition files we must have set labels in nodes.

***Example of creating labels in nodes :** 
```
kubectl label nodes <nodeName> <labelKey>=<labelValue>
kubectl label nodes node-1 size=large
```
<br>

## **Node affintity :**
For example, we would like to say something like place the pod on a large or medium node or something like place the pod on any nodes that are not small. You cannot achieve this using Node selectors for this node affinity and anti affinity features were

**Example of nodeAffinity rules to launch a pod in Large or Medium Nodes :**
```yaml
apiVersion:
kind: pod
metadata:
  name: myapp-pod
spec:
  containers:
  -	name: data-processor
	image: data-processor
  affinity:
	nodeAffinity:
	  requiredDuringSchedulingIgnoreDuringExecution:
		nodeSelectorTerms:
		- matchExpressions:
		  - key: size
			operator: In
			values:
			- Large
			  Medium
```
							
**Example of nodeAffinity rules to not launch a pod in Small Nodes :**
```yaml
apiVersion:
kind: pod
metadata:
  name: myapp-pod
spec:
  containers:
  -	name: data-processor
	image: data-processor
  affinity:
    nodeAffinity:
	  requiredDuringSchedulingIgnoreDuringExecution:
		nodeSelectorTerms:
		- matchExpressions:
		  -	key: size
			operator: NotIn
			values:
			- Small
```				

**Note :** We know that we have only set the labels size to large and medium nodes the smaller nodes don't even have the labels set.So we don't really have to even check the value of the label as long as we are sure we don't set a label size to the smaller nodes using the exists operator will give us the same result. The exists the operator will simply check if the label size exists on the notes and you don't need the values section for that as it does not compare the values. There are a number of other operators as well.

**Example of nodeAffinity rules to launch a pod in Small Nodes :**
```yaml
apiVersion:
kind: pod
metadata:
  name: myapp-pod
spec:
  containers:
  -	name: data-processor
	image: data-processor
  affinity:
	nodeAffinity:
	  requiredDuringSchedulingIgnoreDuringExecution:
	    nodeSelectorTerms:
		- matchExpressions:
		  -	key: size
			operator: Exists
```

### **NodeAffinity Types :**
```
-> requiredDuringSchedulingIgnoreDuringExecution
-> prefferedDuringSchedulingIgnoreDuringExecution
```

## **Resources :** 
Every POD consumes a set of resources.<br>
In this case 2 CPUs , one Memory and some disk space. Whenever a POD is placed on a Node, it consumes resources available to that node. As we have discussed before, it is the kubernetes scheduler that decides which Node a POD goes to. The scheduler takes into consideration, the amount of resources required by a POD. If the node has no sufficient resources, the scheduler avoids placing the POD on that node Instead, places the POD on one where sufficient resources are available if there is no sufficient resources available on any of the nodes, Kubernetes holds back scheduling the POD, and you will see the POD in a pending state. By default, kubernetes assumes that a POD or a container within a POD requires 0.5 CPU & 256 Mebibyte of memory This is known as the resource request. It uses these numbers to identify a node which has sufficient amount of resources available.

Now if you know that your application will need more than these you can modify these values by specifying them in your pod or deployment definition files in the simple pod definition file. Add a section called resources, under which add requests and specify the new values for memory and cpu usage. Kubernetes sets a limit of 1vCPU to containers. So if you do not specify explicitly, a container will be limited to consume only 1 vCPU from the Node. The same goes with memory. By default, kubernetes sets a limit of 512 Mebibyte on containers. If you don't like the default limit you can change them by adding a limit section under the resources section in your pod definition file. Specify new limits for memory and cpu you like this when the pod is created, kubernetes sets new limits for the container. 

Remember that the limits and requests are set for each container within the pod. So what happens when a pod tries to exceed resources beyond its specified limit. In case of the CPU, kubernetes throttles the CPU so that it does not go beyond the specified limit. A container cannot use more CPU resources than its limit. However, this is not the case with memory. A container CAN use more memory resources that its limit. So if a pod tries to consume more memory than its limit constantly, the POD will be terminated


**Note on default resource requirements and limits :**
When a pod is created the containers are assigned a default CPU request of 0.5 and memory of 256Mi, For the POD to pick up those defaults you must have first set those as default values for request and limit by creating a LimitRange in that namespace.

**Example of setting resource limit of memory :**
```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: mem-limit-range
spec:
  limits:
  - default:
      memory: 512Mi
    defaultRequest:
      memory: 256Mi
    type: Container
```
**Example of resource limit of CPUs :**
```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-limit-range
spec:
  limits:
  - default:
      cpu: 1
    defaultRequest:
      cpu: 0.5
    type: Container
```
<br>

**DeamonSet :** 
Daemon set are like replica sets, as it helps you deploy multiple instances of pod. But it runs one copy of your pod on each node in your cluster. Whenever a new node is added to the cluster a replica of the pod is automatically added to that node and when a node is removed the pod is automatically removed. The demon set ensures that one copy of the pod is always present in all nodes in the cluster.

**Example of DeamonSet definition file :**
```yaml
apiversion: apps/v1
kind: DaemonSet
metadata:
  name: myonitoring-daemon
specs:
- template:
	metadata:
	  labels:
		app: myapp
	specs:
	  containers:
	  - name: nginx 
		image: nginx	
selector:
  matchLabels:
    app: monitoring-agent
```			
## **Static Pods :**
Well, the kubelet can manage a node independently when There is no Kubernetes cluster. So there are no Kube API server or anything like that. The one thing that the kubelet knows to do is create PODs. You can configure the kubelet to read the pod definition files from a directory on the server designated to store information about pods. The Kubelet periodically checks this directory for The pods definition files and reads these files and creates pods on the host. Not only does it create the pod it can ensure that the pod stays alive. 

If the application crashes, the kubelet attempts to restart it. If you make a change to any of the file within this directory, the kubelet recreates the pod for those changes to take effect. If you remove a file from this directory the part is deleted automatically. So these PODs that are created by the kubelet on its own without the intervention from the API server or rest of the kuberentes cluster components are known as Static PODs. Remember you can only create PODs this way. You cannot create replicasets or deployments or services by placing a definition file in the designated directory. They are all concepts part of the whole Kubernetes architecture, that requires other control plane components like the replication and deployment controllers etc. The kubelet works at a POD level and can only understand PODs. Which is why it is able to create static pods this way.

So what is that designated folder and how do you configure it. It could be any directory on the host. And the location of that directory is passed in to the kubelet as a option while running the service. The option is named pod manifest path and here it is set to /etc/Kubernetes/manifests. There is also another way to configure this Instead of specifying the option directly in the kubelet.service file, you could provide a path to another config file using the config option, and define the directory path as staticPodPath in that file. 

*Like :*
```
 --config=kubeconfig.yaml\\ (in kubelet.service file)
```
**In kubeconfig.yaml file**
```
staticPodPath: /etc/Kubernetes/manifests
```

## **Multiple Schedulers :**
We have seen how the default-scheduler works in a kubernetes environment It has an algorithm that distributes pods across nodes evenly as well as takes into consideration the various conditions we specify through taints & tolerations and node affinity etc. But what if none of these satisfies your needs? Say you have a specific application that requires its components to be placed on nodes after performing some additional checks. So you decide to have your own scheduling algorithm to place pods on nodes? So that you can add your own custom conditions and checks in it. Kubernetes is highly extensible. You can write your own kubernetes scheduler program, package it and deploy it as the default scheduler or as an additional scheduler in the kubernetes cluster. That way all of the other applications can go through the default scheduler, however one specific application can use your custom scheduler. Your kubernetes cluster can have multiple schedulers at the same time. When creating a POD or a Deployment you can instruct kubernetes to have the POD scheduled by a specific scheduler.

```
--Due definition file--
```
Finally an important option to look here is the leader-elect option. The leader-elect option is used when you have multiple copies of the scheduler running on different master nodes, in a High Availability setup where you have multiple master nodes with the kube-scheduler process running on both of them. If multiple copies of the same scheduler are running on different nodes only one can be active at a time. That’s where the leader-elect option helps in choosing a leader who will lead scheduling activities.

