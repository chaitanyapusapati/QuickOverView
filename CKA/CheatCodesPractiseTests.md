# Practice Test - PODs
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-pods/)

## Here are the solutions to the practice test
1. Run the command **`kubectl get pods`** and count the number of pods.
   <details>

   ```
   $ kubectl get pods
   ```
   </details>
   
1. Run the command **`kubectl run nginx --image=nginx`**.
   <details>

   ```
   $ kubectl run nginx --image=nginx
   ```
   </details>

1. Run the command **`kubectl get pods`** and count the number of pods.

   <details>

   ```
   $ kubectl get pods --no-headers | wc -l
   ```
   </details>

1. Run the command **`kubectl describe pod newpods`** look under the containers section.

   <details>

    ```
    $ kubectl describe pod newpods | grep -w Image
    ```
   </details>

1. Run the command **`kubectl describe pod newpods`** look into the `Node` section at the very beginning or simply run the command **`kubectl get pods -o wide`**.

   <details>

    ```
    $ kubectl describe pod newpods
    ```
   </details>

1. Run the command **`kubectl describe pod webapp`** and look under the Containers section (or) Run **`kubectl get pods`** and look under the READY section.

   <details>

   ```
   $ kubectl describe pod webapp
   ```
   
   </details>

1. Run the command **`kubectl describe pod webapp`** and look under the containers section.
   
   <details>

   ```
   $ kubectl describe pod webapp
   ```
   </details>

1. Run the command **`kubectl describe pod webapp`** and look under the containers section.

   <details>

   ```
   $ kubectl describe pod webapp
   ```
   </details>

1. Run the command **`kubectl describe pod webapp`** and look under the events section.

   <details>

   ```
   $ kubectl describe pod webapp
   ```
   
   </details>

1. Run the command **`kubectl get pods`**.
   
   <details>

   ```
   $ kubectl get pods
   ```
   
   </details>

1. Run the command **`kubectl delete pod webapp`**.

   <details>
   To delete the pod without any delay and confirmation, we can add --force flag.
  
   ```
   $ kubectl delete pod webapp --force
   ```
   
   </details>

1. Create a pod definition YAML file and use it to create a POD or use the command **`kubectl run redis --image=redis123`**.

   <details>
   To create a pod definition yaml file:
  
   ```
   $ kubectl run redis --image=redis123 --dry-run=client -oyaml > redis.yaml
   
   $ kubectl create -f redis.yaml
   ```
   
   </details>

1. Now fix the image on the pod to **`redis`**. Update the pod-definition file and use **`kubectl apply`** command or use **`kubectl edit pod redis`** command.

   <details>

   ```
   Fix the image name in the redis.yaml file and apply the changes.
   
   $ kubectl apply -f redis.yaml
   
   Direct edit in the running pod.
   
   $ kubectl edit pod redis
   ```
   
   </details>

<br><br>

# Practice Test - ReplicaSets
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-replicasets/)
  
#### Solutions for the replicaset practice tests
1. Run the command **`kubectl get pods`** and count the number of pods.
   <details>

   ```
   $ kubectl get pods
   ```
   </details>

1. Run the command **`kubectl get replicaset`** and count the number of replicasets.
   
   <details>

   ```
   $ kubectl get rs
   ```
   </details>

1. Run the command **`kubectl get replicaset`**
   
   <details>

   ```
   $ kubectl get rs
   ```
   </details>

1. Run the command **`kubectl get replicaset`** and look at the count under the **`Desired`** column

   <details>

   ```
   $ kubectl get rs
   ```
   </details>

1. Run the command **`kubectl describe replicaset`** and look under the containers section.
   
   <details>

   ```
   $ kubectl describe replicaset (or)
   $ kubectl get rs -o wide
   ```
   </details>

1. Run the command **`kubectl get replicaset`** and look at the count under the **`Ready`** column

   <details>

   ```
   $ kubectl get replicaset
   ```
   </details>

1. Run the command **`kubectl describe pods`** and look under the events section.
   
   <details>

   ```
   $ kubectl describe pods
   ```
   </details>

1. Run the command **`kubectl delete pod <podname>`**

   <details>

   ```
   $ kubectl delete pod new-replica-set-XXXX
   ```
   </details>

1. Run the command **`kubectl get pods`** and count the number of PODs
   
   <details>

   ```
   $ kubectl get pods
   ```
   </details>

1. ReplicaSets ensures that desired number of PODs always run

1. The value for **`apiVersion`** is incorrect. Find the correct apiVersion for ReplicaSet.

   Get the apiVersion for replicaset
   
   <details>

   ```
   $ kubectl explain replicaset|grep VERSION
   ```
   </details>

   Update the replicaset definition file with correct version and create a replicaset
    
   <details>

   ```
   $ kubectl create -f replicaset-definition-1.yaml
   ```
   </details>

1. The values for labels on lines 9 and 13 should match.
   <details>

   ```
   Selector matchLabels should match with POD labels - Update the replicaset-definition-2.yaml
   $ kubectl create -f replicaset-definition-2.yaml
   ```
   </details>

1. Run the command **`kubectl delete replicaset`**
   
   <details>

   ```
   $ kubectl delete replicaset replicaset-1
   $ kubectl delete rs replicaset-2
   ```
   </details>

1. Run the command **`kubectl edit replicaset new-replica-set`**, modify the image name to **`busybox`** and then save the file.
   
   <details>

   ```
   $ kubectl edit replicaset new-replica-set
   ```
   </details>

1. Run the command **`kubectl edit replicaset new-replica-set`**, modify the replicas and then save the file.
   
   <details>

   ```
   $ kubectl edit replicaset new-replica-set
   ```
   </details>

   Another way
   
   <details>
   
   ```
   $ kubectl scale --replicas=5 replicaset new-replica-set
   ```
   </details>

1. Run the command **`kubectl edit replicaset new-replica-set`**, modify the replicas and then save the file.

   <details>

   ```
   $ kubectl edit replicaset new-replica-set
   ```
   </details>

   Another way
   
   <details>

   ```
   $ kubectl scale --replicas=2 replicaset new-replica-set
   ```
   </details>

<br><br><br>

# Practice Test - Deployments
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-tests-deployments/)
  
Solutions to the deploments practice test
1. Run the command **`kubectl get pods`** and count the number of pods.
   
   <details>

   ```
   $ kubectl get pods
   ```
   </details>

1. Run the command **`kubectl get replicaset`** and count the number of ReplicaSets.
   
   <details>

   ```
   $ kubectl get replicaset (or)
   $ kubectl get rs
   ```
   </details>

1. Run the command **`kubectl get deployment`** and count the number of Deployments.
   
   <details>

   ```
   $ kubectl get deployment
   ```
   </details>

1. Run the command **`kubectl get deployment`** and count the number of Deployments.
   
   <details>

   ```
   $ kubectl get deployment
   ```
   </details>

1. Run the command **`kubectl get replicaset`** and count the number of ReplicaSets.
   
   <details>

   ```
   $ kubectl get replicaset (or)
   $ kubectl get rs
   ```
   </details>

1. Run the command **`kubectl get pods`** and count the number of PODs.
   
   <details>

   ```
   $ kubectl get pods
   ```
   </details>

1. Run the command **`kubectl get deployment`** and count the number of PODs.
   
   <details>

   ```
   $ kubectl get deployment
   ```
   </details>

1. Run the command **`kubectl describe deployment`** and look under the containers section.

   <details>

   ```
   $ kubectl describe deployment
   ```
   </details>

   Another way
   
   <details>

   ```
   $ kubectl get deployment -o wide
   ```
   </details>

1. Run the command **`kubectl describe pods`** and look under the events section.

   <details>

   ```
   $ kubectl describe pods
   ```
   </details>

1. Run the command **`kubectl describe pods`** and look under the events section.
   
   <details>

   ```
   $ kubectl describe pods
   ```
   </details>

1. The value for **`kind`** is incorrect. It should be **`Deployment`** with a capital **`D`**. Update the deployment definition and create the deployment.

   <details>

   ```
   $ kubectl create -f deployment-definition-1.yaml
   ```
   </details>

1. Run the command below command
 
   <details>

   ```
   $ kubectl create deployment httpd-frontend --image=httpd:2.4-alpine 
   $ kubectl scale deplyoment httpd-frontend --replicas=3
   ```
   </details>

<br><br><br>

# Practice Test - Namespaces
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-namespaces/)

Solutions to practice test for namespaces

1. Run the command **`kubectl get namespace`** and count the number of pods.
   
   <details>

   ```
   $ kubectl get namespace
   ```
   </details>

1. Run the command **`kubectl get pods --namespace=research`**
   
   <details>

   ```
   $ kubectl get pods --namespace=research
   ```
   </details>

1. Run the below command

   <details>

   ```
   $ kubectl run redis --image=redis --namespace=finance
   ```
   </details>

1. Run the command **`kubectl get pods --all-namespaces`**

   <details>

   ```
   $ kubectl get pods --all-namespaces
   ```
   </details>

1. Connectivity Test
   
   <details>

   ```
   Host Name: db-service and Host Port: 3306
   ```
   </details>

1. Connectivity Test

   <details>

   ```
   Host Name: db-service.dev.svc.cluster.local and Host Port: 3306
   ```
   </details>

<br><br><br>

# Practice Test - Services
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-services/)

#### Solutions to Practice test - Services

- Run the command **`kubectl get services`** and count the number of services.
  
  <details>

  ```
  $ kubectl get services
  ```
  </details>

- Run the command **`kubectl get services`** and look at the Type column

  <details>

  ```
  $ kubectl get services
  ```
  </details>

- Run the command **`kubectl describe service`** and look at TargetPort.

  <details>

  ```
  $ kubectl describe service|grep TargetPort
  ```
  </details>

- Run the command **`kubectl describe service`** and look at Labels

  <details>

  ```
  $ kubectl describe service
  ```
  </details>

- Run the command **`kubectl describe service`** and look at Endpoints
  
  <details>

  ```
  $ kubectl describe service
  ```
  </details>

- Run the command **`kubectl get deployment`** and count the number of pods.

  <details>

  ```
  $ kubectl get deployment
  ```
  </details>

- Run the command **`kubectl describe deployment`** and look under the containers section.

  <details>

  ```
  $ kubectl describe deployment
  ```
  </details>

- Try to access the Web Application UI using the tab simple-webapp-ui above the terminal.

- Update the given values in the service definition file and create the service.

  <details>

  ```
  $ kubectl create -f service-definition-1.yaml
  ```
  </details>

<br><br><br>

# Practice Test - Imperative Commands
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-imperative-commands-2/)
  
Solutions for Practice Test - Imperative Commands

- Run the command **`kubectl run nginx-pod --image=nginx:alpine`**. 
  
  <details>

  ```
  $ kubectl run nginx-pod --image=nginx:alpine
  ```
  </details>

- Run the command **`kubectl run redis --image=redis:alpine -l tier=db`**.

  <details>

  ```
  $ kubectl run redis --image=redis:alpine -l tier=db
  ```
  </details>

- Run the command **`kubectl expose pod redis --port=6379 --name redis-service`**.

  <details>

  ```
  $ kubectl expose pod redis --port=6379 --name redis-service
  ```
  </details>

- Run the command **`kubectl create deployment webapp --image=kodekloud/webapp-color`**. Then scale the webapp to 3 using command **`kubectl scale deployment/webapp --replicas=3`**.

  <details>

  ```
  $ kubectl create deployment webapp --image=kodekloud/webapp-color
  $ kubectl scale deployment/webapp --replicas=3
  ```
  </details>

- Run the command **`kubectl run custom-nginx --image=nginx --port=8080`**.

  <details>

  ```
  $ kubectl run custom-nginx --image=nginx --port=8080
  ```
  </details>

- Run the command **`kubectl create ns dev-ns`**.
  
  <details>

  ```
  $ kubectl create ns dev-ns
  ```
  </details>

- Run the command to create a deployment.

  <details>

  ```
  Step 1: Create the deployment YAML file
  $ kubectl create deployment redis-deploy --image redis --namespace=dev-ns --dry-run=client -o yaml > deploy.yaml
  $ kubectl create -f deploy.yaml

  Step 2: Edit the YAML file and add update the replicas to 2.
  
  Step 3: Run kubectl apply -f deploy.yaml to create the deployment in the dev-ns namespace.
  $ kubectl apply -f deploy.yaml

  You can also use kubectl scale deployment or kubectl edit deployment to change the number of replicas once the object has been created.
  $ kubectl edit deployment redis-deploy
  $ kubectl scale deployment/redis-deploy --replicas=2 --namespace=dev-ns
  
  In v1.19, kubectl create deployment supports "--replicas" flag to increase the count number.
  $ kubectl create deployment redis-deploy --image=redis --namespace=dev-ns --replicas=2 
  ```
  </details>

- First create a YAML file for both the pod and service like this: **`kubectl run httpd --image=httpd:alpine --port=80 --expose`**.

  <details>

  ```
  $ kubectl run httpd --image=httpd:alpine --port=80 --expose
  ```
  </details>

  <br><br><br>

# Practice Test - Manual Scheduling
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-manual-scheduling/)

Solutions to Practice Test - Manual Scheduling

- Run, **`kubectl create -f nginx.yaml`**
  
  <details>

  ```
  $ kubectl create -f nginx.yaml
  ```
  </details>

- Run the command 'kubectl get pods' and check the status column

  <details>

  ```
  $ kubectl get pods
  ```
  </details>

- Run the command 'kubectl get pods --namespace kube-system'

  <details>

  ```
  $ kubectl get pods --namespace kube-system
  ```
  </details>

- Set **`nodeName`** property on the pod to node01 node

  <details>

  ```
  $ vi nginx.yaml
  $ kubectl delete -f nginx.yaml
  $ kubectl create -f nginx.yaml
  ```
  </details>

- Set **`nodeName`** property on the pod to master node

  <details>

  ```
  $ vi nginx.yaml
  $ kubectl delete -f nginx.yaml
  $ kubectl create -f nginx.yaml
  ```
  </details>

 <br><br><br>

# Practice Test - Labels and Selectors
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-labels-and-selectors/)
  
Solutions to Practice Test - Labels and Selectors
- Run the command 'kubectl get pods --selector env=dev'
  
  <details>

  ```
  $ kubectl get pods --selector env=dev
  ```
  </details>

- Run the command 'kubectl get pods --selector bu=finance'

  <details>

  ```
  $ kubectl get pods --selector bu=finance
  ```
  </details>

- Run the command 'kubectl get all --selector env=prod'

  <details>

  ```
  $ kubectl get all --selector env=prod
  ```
  </details>

- Run the command 'kubectl get all --selector env=prod,bu=finance,tier=frontend'
  
  <details>

  ```
  $ kubectl get all --selector env=prod,bu=finance,tier=frontend
  ```
  </details>

- Set the labels on the pod definition template to frontend

  <details>

  ```
  $ vi replicaset-definition.yaml
  $ kubectl create -f replicaset-definition.yaml
  ```
  </details>

  <br><br><br>

# Practice Test - Taints and Tolerations
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-taints-and-tolerations/)
  
Solutions to the Practice Test - Taints and Tolerations

- Run the command 'kubectl get nodes' and count the number of nodes.
  
  <details>

  ```
  $ kubectl get nodes
  ```
  </details>

- Run the command 'kubectl describe node node01' and see the taint property

  <details>

  ```
  $ kubectl describe node node01
  ```
  </details>

- Run the command 'kubectl taint nodes node01 spray=mortein:NoSchedule'.

  <details>

  ```
  $ kubectl taint nodes node01 spray=mortein:NoSchedule
  ```
  </details>

- Answer file at /var/answers/mosquito.yaml

  <details>

  ```
  master $ cat /var/answers/mosquito.yaml
  apiVersion: v1
  kind: Pod
   metadata:
    name: mosquito
  spec:
   containers:
   - image: nginx
     name: mosquito
  ```
  ```
  $ kubectl create -f /var/answers/mosquito.yaml
  ```
  </details>

- Run the command 'kubectl get pods' and see the state

  <details>

  ```
  $ kubectl get pods
  ```
  </details>

- Why do you think the pod is in a pending state?

  <details>

  ```
  POD Mosquito cannot tolerate taint Mortein
  ```
  </details>

- Answer file at /var/answers/bee.yaml

  <details>

  ```
  master $ cat /var/answers/bee.yaml
  apiVersion: v1
  kind: Pod
  metadata:
   name: bee
  spec:
   containers:
   - image: nginx
     name: bee
   tolerations:
   - key: spray
     value: mortein
     effect: NoSchedule
     operator: Equal
  ```
  ```
  $ kubectl create -f /var/answers/bee.yaml
  ```
  </details>

- Notice the 'bee' pod was scheduled on node node01 despite the taint.

- Run the command 'kubectl describe node master' and see the taint property
  
  <details>

  ```
  $ kubectl describe node master
  ```
  </details>

- Run the command 'kubectl taint nodes master node-role.kubernetes.io/master:NoSchedule-'.
  
  <details>

  ```
  $ kubectl taint nodes master node-role.kubernetes.io/master:NoSchedule-
  ```
  </details>

- Run the command 'kubectl get pods' and see the state

  <details>

  ```
  $ kubectl get pods
  ```
  </details>

- Run the command 'kubectl get pods -o wide' and look at the Node column
 
  <details>

  ```
  $ kubectl get pods -o wide
  ```
  </details>

<br><br><br>

# Practice Test - Node Affinity
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-node-affinity-2/)
  
Solutions to practice test - node affinity

- Run the command 'kubectl describe node node01' and count the number of labels under **`Labels Section`**.
  
  <details>

  ```
  $ kubectl describe node node01
  ```
  </details>

- Run the command 'kubectl describe node node01' and see the label section
  
  <details>

  ```
  $ kubectl describe node node01
  ```
  </details>

- Run the command 'kubectl label node node01 color=blue'.

  <details>

  ```
  $ kubectl label node node01 color=blue
  ```
  </details>

- Run the below commands

  <details>

  ```
  $ kubectl create deployment blue --image=nginx
  $ kubectl scale deployment blue --replicas=6
  ```
  </details>

- Check if master and node01 have any taints on them that will prevent the pods to be scheduled on them. If there are no taints, the pods can be scheduled on either node.
  
  <details>

  ```
  $ kubectl describe nodes|grep -i taints
  $ kubectl get pods -o wide
  ```
  </details>

- Answer file at /var/answers/blue-deployment.yaml
  
  <details>

  ```
  $ kubectl edit deployment blue
  ```
  </details>

  Add the below under the template.spec section
  
  <details>

  ```
  affinity:
      nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: color
                operator: In
                values:
                - blue
   ```
   </details>

 - Run the command 'kubectl get pods -o wide' and see the Node column
   
   <details>

   ```
   $ kubectl get pods -o wide
   ```
   </details>

 - Answer file at /var/answers/red-deployment.yaml
   Add the below under the template.spec section
   
   <details>

   ```
   affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: node-role.kubernetes.io/master
                operator: Exists
   ```
   ```
   $ kubectl create -f red-deployment.yaml
   ```
   ```
   $ kubectl get pods -o wide
   ```
   </details>
   
  <br><br><br>

  # Practice Test - Resource Limits
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-resource-limits/)
  
Solutions to practice test - resource limtis
- Run the command 'kubectl describe pod rabbit' and inspect requests.
  
  <details>

  ```
  $ kubectl describe pod rabbit
  ```
  </details>

- Run the command 'kubectl delete pod rabbit'.

  <details>

  ```
  $ kubectl delete pod rabbit
  ```
  </details>

- Run the command 'kubectl get pods' and inspect the status of the pod elephant

  <details>

  ```
  $ kubectl get pods
  ```
  </details>

- The status 'OOMKilled' indicates that the pod ran out of memory. Identify the memory limit set on the POD.

- Generate a template of the existing pod.

  <details>

  ```
  $ kubectl get pods elephant -o yaml > elephant.yaml
  ```
  </details>

  Update the elephant.yaml pod definition with the resource memory limits to 20Mi
  
  <details>

  ```
  resources:
      limits:
        memory: 20Mi
  ---
  ```
  </details>

  Delete the pod and recreate it.
  
  <details>

  ```
  $ kubectl delete pod elephant
  $ kubectl create -f elephant.yaml
  ```
  </details>

- Inspect the status of POD. Make sure it's running
  
  <details>

  ```
  $ kubectl get pods
  ```
  </details>

- Run the command 'kubectl delete pod elephant'.

  <details>

  ```
  $ kubectl delete pod elephant
  ```
  </details>

<br><br><br>

# Practice Test - DaemonSets
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-daemonsets/)
  
Solutions to practice test daemonsets
- Run the command kubectl get daemonsets --all-namespaces
  
  <details>

  ```
  $ kubectl get daemonsets --all-namespaces
  ```
  </details>

- Run the command kubectl get daemonsets --all-namespaces

  <details>

  ```
  $ kubectl get daemonsets --all-namespaces
  ```
  </details>

- Run the command kubectl get all --all-namespaces and identify the types

  <details>

  ```
  $ kubectl get all --all-namespaces
  ```
  </details>

- Run the command kubectl describe daemonset kube-proxy --namespace=kube-system

  <details>

  ```
  $ kubectl describe daemonset kube-proxy --namespace=kube-system
  ```
  </details>

- Run the command kubectl describe daemonset kube-flannel-ds-amd64 --namespace=kube-system

  <details>

  ```
  $ kubectl describe daemonset kube-flannel-ds-amd64 --namespace=kube-system
  ```
  </details>
    
- Create a daemonset

  <details>

  ```
  $ vi ds.yaml
  ```

  ```
  apiVersion: apps/v1
  kind: DaemonSet
  metadata:
    name: elasticsearch
    namespace: kube-system
    labels:
      k8s-app: fluentd-logging
  spec:
    selector:
      matchLabels:
        name: elasticsearch
    template:
      metadata:
        labels:
          name: elasticsearch
      spec:
        tolerations:
        # this toleration is to have the daemonset runnable on master nodes
        # remove it if your masters can't run pods
        - key: node-role.kubernetes.io/master
          effect: NoSchedule
        containers:
        - name: elasticsearch
          image: k8s.gcr.io/fluentd-elasticsearch:1.20
  ```
  </details>

- To create the daemonset and list the daemonsets and pods

  <details>

  ```
  $ kubectl create -f ds.yaml
  $ kubectl get ds -n kube-system
  $ kubectl get pod -n kube-system|grep elasticsearch
  ```
  </details>

<br><br><br>

# Practice Test - Static Pods
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-static-pods/)
  
Solutions to the practice test - static pods
- Run the command kubectl get pods --all-namespaces and look for those with -master appended in the name
  
  <details>

  ```
  $ kubectl get pods --all-namespaces
  ```
  </details>

- Which of the below components is NOT deployed as a static pod?

  <details>

  ```
  $ kubectl get pods --all-namespaces
  ```
  </details>

- Which of the below components is NOT deployed as a static POD?

  <details>

  ```
  $ kubectl get pods --all-namespaces
  ```
  </details>

- Run the kubectl get pods --all-namespaces -o wide

  <details>

  ```
  $ kubectl get pods --all-namespaces -o wide
  ```
  </details>

- Run the command ps -aux | grep kubelet and identify the config file - --config=/var/lib/kubelet/config.yaml. Then checkin the config file for staticPdPath.

  <details>

  ```
  $ ps -aux | grep kubelet
  ```
  </details>

- Count the number of files under /etc/kubernetes/manifests

- Check the image defined in the /etc/kubernetes/manifests/kube-apiserver.yaml manifest file.

- Create a pod definition file in the manifests folder. Use command kubectl run --restart=Never --image=busybox static-busybox --dry-run -o yaml --command -- sleep 1000 > /etc/kubernetes/manifests/static-busybox.yaml
  
  <details>

  ```
  $ kubectl run --restart=Never --image=busybox static-busybox --dry-run=client -o yaml --command -- sleep 1000 > /etc/kubernetes/manifests/static-busybox.yaml
  ```
  </details>

- Simply edit the static pod definition file and save it 

  <details>

  ```
  /etc/kubernetes/manifests/static-busybox.yaml
  ```
  </details>

  OR
  
  <details>

  ```
  Run the command with updated image tag:
  kubectl run --restart=Never --image=busybox:1.28.4 static-busybox--dry-run=client -o yaml --command -- sleep 1000 > /etc/kubernetes/manifests/static-busybox.yaml
  ```
  </details>

- Identify which node the static pod is created on, ssh to the node and delete the pod definition file. If you don't know theIP of the node, run the kubectl get nodes -o wide command and identify the IP. Then SSH to the node using that IP. For static pod manifest path look at the file /var/lib/kubelet/config.yaml on node01

  <details>

  ```
  $ kubectl get pods -o wide
  $ kubectl get nodes -o wide
  $ ssh <ip address of pod>
  $ grep staticPodPath /var/lib/kubelet/config.yaml
  $ node01 $ rm -rf /etc/just-to-mess-with-you/greenbox.yaml
  ```
  </details>

<br><br><br>

# Practice Test - Multiple Schedulers
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-multiple-schedulers/)
  
Solutions to practice test - multiple schedulers
- Run the command 'kubectl get pods --namespace=kube-system'
  
  <details>

  ```
  $ kubectl get pods --namespace=kube-system
  ```
  </details>

- Run the command 'kubectl describe pod kube-scheduler-master --namespace=kube-system'

  <details>

  ```
  $ kubectl describe pod kube-scheduler-master --namespace=kube-system
  ```
  </details>

- Use the file at /etc/kubernetes/manifests/kube-scheduler.yaml to create your own scheduler. View answer file at /var/answers

  <details>

  ```
  $ kubectl create -f my-scheduler.yaml
  ```
  </details>

- Set schedulerName property on pod specification to the name of the new scheduler. File is located at /root/nginx-pod.yaml
  
  <details>

  ```
  master $ grep schedulerName /root/nginx-pod.yaml
  schedulerName: my-scheduler
  
  $ kubectl create -f /root/nginx-pod.yaml
  ```
  </details>

<br><br><br>

# Practice Test - Monitor Cluster Components
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-monitor-cluster-components/)
  
Solutions to practice test - monitor cluster components
- We have deployed a few PODs running workloads. Inspect it.

  <details>
  
  ```
  $ kubectl get pods
  ```
  </details>
  
- Let us deploy metrics-server to monitor the PODs and Nodes. Pull the git repository for the deployment files.

  <details>
  
  ```
  $ git clone https://github.com/kodekloudhub/kubernetes-metrics-server.git
  ```
  </details>
  
- Run the 'kubectl create -f .' command from within the downloaded repository.

  <details>
  
  ```
  $ cd kubernetes-metrics-server
  $ kubectl create -f .
  ```
  </details>
    
- Run the 'kubectl top node' command and wait for a valid output.

  <details>
  
  ```
  $ kubectl top node
  ```
  </details>
  
- Run the 'kubectl top node' command

  <details>
  
  ```
  $ kubectl top node
  ```
  </details>
  
- Run the 'kubectl top node' command
  
  <details>
  
  ```
  $ kubectl top node
  ```
  </details>
  
- Run the 'kubectl top pod' command
  
  <details>
  
  ```
  $ kubectl top pod
  ```
  </details>
  
- Run the 'kubectl top pod' command
  
  <details>
  
  ```
  $ kubectl top pod
  ```
  </details>
  
<br><br><br>

# Practice Test - Managing Application Logs
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-managing-application-logs/)
  
Solutions to practice test - managing application logs
- We have deployed a POD hosting an application. Inspect it. Wait for it to start.

  <details>
  
  ```
  $ kubectl get pods
  ```
  </details>
  
- Inspect the logs of the POD
  
  <details>
  
  ```
  $ kubectl logs webapp-1
  ```
  </details>
  
- We have deployed a new POD - 'webapp-2' - hosting an application. Inspect it. Wait for it to start.

  <details>
  
  ```
  $ kubectl get pods
  ```
  </details>
  
- Inspect the logs of the webapp in the POD
  
  <details>
  
  ```
  $ kubectl logs webapp-2
  ```
  </details>

<br><br><br>

# Practice Test - Rolling Updates and Rollback
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-rolling-updates-and-rollbacks/)
  
Solutions to practice test - rolling updates and rollback
- We have deployed a simple web application. Inspect the PODs and the Services

  <details>
  
  ```
  $ kubectl get pods
  $ kubectl get services
  ```
  </details>
  
- What is the current color of the web application?
  
  <details>
  
  ```
  Access the web portal
  ```
  </details>
    
- Execute the script at /root/curl-test.sh.

- Run the command 'kubectl describe deployment' and look at 'Desired Replicas'

  <details>
  
  ```
  $ kubectl describe deployment
  ```
  </details>
  
- Run the command 'kubectl describe deployment' and look for 'Images'
  
  <details>
  
  ```
  $ kubectl describe deployment
  ```
  </details>
  
- Run the command 'kubectl describe deployment' and look at 'StrategyType'
  
  <details>
  
  ```
  $ kubectl describe deployment
  ```
  </details>
  
- If you were to upgrade the application now what would happen?
  
  <details>
  
  ```
  PODs are upgraded few at a time
  ```
  </details>
  
- Run the command 'kubectl edit deployment frontend' and modify the required feild
  
  <details>
  
  ```
  $ kubectl edit deployment frontend
  ```
  </details>
    
- Execute the script at /root/curl-test.sh.

- Look at the Max Unavailable value under RollingUpdateStrategy in deployment details

  <details>
  ```
  $ kubectl describe deployment
  ```
  </details>
  
- Run the command 'kubectl edit deployment frontend' and modify the required field. Make sure to delete the properties of rollingUpdate as well, set at 'strategy.rollingUpdate'.
  
  <details>
  
  ```
  $ kubectl edit deployment frontend]
  ```
  
  </details>
  
- Run the command 'kubectl edit deployment frontend' and modify the required feild

  <details>
  
  ```
  $ kubectl edit deployment frontend
  ```
  </details>
  
- Execute the script at /root/curl-test.sh.

<br><br><br>

# Practice Test - Commands and Arguments
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-commands-and-arguments/)
  
Solutions to practice test - commands and arguments
- Run the command 'kubectl get pods' and count the number of pods.
  
  <details>
  
  ```
  $ kubectl get pods
  ```
  </details>
  
- Run the command 'kubectl describe pod' and look for command option

  <details>
  
  ```
  $ kubectl describe pod
  ```
  </details>
  
- Set the command option to ['sleep', '5000']. Answer file at: /var/answers/answer-ubuntu-sleeper-2.yaml

- Both sleep and 1200 should be defined as a string. Answer file at: /var/answers/answer-ubuntu-sleeper-3.yaml

- Answer file at: /var/answers/answer-ubuntu-sleeper-3-2.yaml

- Inspect the file 'Dockerfile' given at /root/webapp-color. What command is run at container startup?
  
  <details>
  
  ```
  python app.py
  ```
  </details>
  
- Inspect the file 'Dockerfile2' given at /root/webapp-color. What command is run at container startup?

  <details>
  ```
  python app.py --color red
  ```
  </details>
  
- The 'command' (entrypoint) is overridden in the pod definition. So the answer is --color green

- Inspect the two files under directory 'webapp-color-3'. What command is run at container startup?

  <details>
  
  ```
  python app.py --color pink
  ```
  </details>
  
- Answer file located at /var/answers/answer-webapp-color-green.yaml

<br><br><br>

# Practice Test Env Variables
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-env-variables/)
  
Solutions to practice test env variables
- Run the command 'kubectl get pods' and count the number of pods.
  
  <details>
  
  ```
  $ kubectl get pods
  ```
  
  </details>
  
- Run the command 'kubectl describe pod' and look for ENV option

  <details>
  
  ```
  $ kubectl describe pod
  ```
  
  </details>
  
- Run the command 'kubectl describe pod' and look for ENV option
  
  <details>
  
  ```
  $ kubectl describe pod
  ```
  
  </details>
    
- View the web application UI by clicking on the 'Webapp Color' Tab above your terminal.

- Set the environment option to APP_COLOR - green.
  
  <details>
  
  ```
  $ kubectl get pods webapp-color -o yaml > green.yaml
  $ kubectl delete pods webapp-color
  Update APP_COLOR to green
  $ kubectl create -f green.yaml
  ```
  
  </details>
  
- View the changes to the web application UI by clicking on the 'Webapp Color' Tab above your terminal.

- Run kubectl get configmaps
  
  <details>
  
  ```
  $ kubectl get configmaps
  ```
  
  </details>
  
- Run the command 'kubectl describe configmaps' and look for DB_HOST option

  <details>
  
  ```
  $ kubectl describe configmaps
  ```
  
  </details>
  
- Create a new ConfigMap for the 'webapp-color' POD. Use the spec given on the right.

  <details>
  
  ```
  $ kubectl create configmap webapp-config-map --from-literal=APP_COLOR=darkblue
  ```
  
  </details>
  
- Set the environment option to envFrom and use configMapRef webapp-config-map.
  
  <details>
  
  ```
  $ kubectl get pods webapp-color -o yaml > new-webapp.yaml
  $ kubectl delete pods webapp-color
   Update pod definition file, under spec.containers section update the below.
  - envFrom:
    - configMapRef:
       name: webapp-config-map
  ```
  
  </details>
  
  <details>
  
  ```
  $ kubectl create -f new-webapp.yaml
  ``` 
  
  </details>

- View the changes to the web application UI by clicking on the 'Webapp Color' Tab above your terminal.

<br><br><br>

# Practice Test - Secrets
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-secrets/)

Solutions for pracice test - Secrets
- Run the command 'kubectl get secrets' and count the number of pods.
  
  <details>
  ```
  $ kubectl get secrets
  ```
  </details>
    
- Run the command 'kubectl get secrets' and look at the DATA field

  <details>
  ```
  $ kubectl get secrets
  ```
  </details>
  
- Run the command 'kubectl describe secret'

  <details>
  ```
  $ kubectl describe secret
  ```
  </details>
    
- Run the command 'kubectl describe secret'

  <details>
  ```
  $ kubectl describe secret
  ```
  </details>
  
- We have already deployed the required pods and services. Check out the pods and services created. Check out the web application using the 'Webapp MySQL' link above your terminal, next to the Quiz Portal Link.

- Run command kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --from-literal=DBUser=root --from-literal=DB_Password=password123

  <details>
  ```
  $ kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --from-literal=DB_User=root --from-literal=DB_Password=password123
  ```
  </details>
  
- Check Answer at /var/answers/answer-webapp.yaml

  <details>
  ```
  $ kubectl get pod webapp-pod -o yaml > web.yaml
  $ kubectl delete pod webapp-pod
  ```
  </details>
  
  Update web.yaml with secret section
  
  envFrom:
  - secretRef:
      name: db-secret
  
  <details>
  ```
  $ kubectl create -f web.yaml
  ```
  </details>
  
- View the web application to verify it can successfully connect to the database

<br><br><br>

# Practice Test - Multi-Container Pods
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-multi-container-pods/)
  
Solutions to practice test - multi-container pods
- Identify the number of containers running in the 'red' pod.
  
  <details>
  
  ```
  $ kubectl get pod red
  ```
  </details>
  
- Identify the name of the containers running in the 'blue' pod.

  <details>
  ```
  $ kubectl describe pod blue
  ```
  </details>
    
- Answer file is located at /var/answers/answer-yellow.yaml

  <details>
  ```
  $ kubectl create -f /var/answers/answer-yellow.yaml
  ```
  </details>
  
- We have deployed an application logging stack in the elastic-stack namespace. Inspect it.
  
  <details>
  ```
  $ kubectl get pods -n elastic-stack
  ```
  </details>
  
- Inspect the Kibana UI using the link above your terminal. There shouldn't be any logs for now.

- Run `kubectl describe pod -n elastic-stack`

  <details>
  ```
  $ kubectl describe pod -n elastic-stack
  ```
  </details>
  
- Run the command 'kubectl -n elastic-stack exec -it app cat /log/app.log'
  
  <details>
  ```
  $ kubectl -n elastic-stack exec -it app cat /log/app.log
  ```
  </details>
  
- Answer file is located at /var/answers/answer-app.yaml
  
- Inspect the Kibana UI. You should now see logs appearing in the 'Discover' section. You might have to wait for a couple of minutes for the logs to populate. You might have to create an index pattern to list the logs. If not sure check this video: https://bit.ly/2EXYdHf

<br><br><br>

# Practice Test - Init-Containers
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-init-containers/)
  
Solutions to practice test - init-containers
- Identify the pod that has an initContainer configured.

  <details>
  ```
  $ kubectl get pods
  $ kubectl describe pods
  ```
  </details>
  
- What is the image used by the initContainer on the blue pod?
  
  <details>
  ```
  $ kubectl describe pods blue
  ```
  </details>
    
- Run the command kubectl describe pod blue and check the state field of the initContainer.

  <details>
  ```
  $ kubectl describe pod blue
  ```
  </details>
  
- Check the reason field of the initContainer
  
  <details>
  ```
  $ kubectl describe pod blue
  ```
  </details>
  
- Run the command kubectl describe pod purple
  
  <details>
  ```
  $ kubectl describe pod purple
  ```
  </details>
  
- Run the kubectl describe pod purple command and look at the container state
  
  <details>
  ```
  $ kubectl describe pod purple
  ```
  </details>
  
- Check the commands used in the initContainers. The first one sleeps for 600 seconds (10 minutes) and the second one sleeps for 1200 seconds (20 minutes)
  
  <details>
  ```
  $ kubectl describe pod purple
  ```
  </details>
  
- Update the pod red to use an initContainer that uses the busybox image and sleeps for 20 seconds
  
  <details>
  ```
  $ kubectl get pod red -o yaml > red.yaml
  $ kubectl delete pod red
  ```
  </details>
  
  Update the red.yaml with sleep 20 seconds
  
  <details>
  ```
  $ kubectl create -f red.yaml
  ```
  </details>
  
- Check the command used by the initContainer. Looks like there is a type in sleep command. Fix it, it should be **`sleep 2`** not **`sleeeep 2`**
  
  <details>
  ```
  $ kubectl describe pod orange
  $ kubectl get pod orange -o yaml > orange.yaml
  $ kubectl delete pod orange
  
  Update the orange.yaml with correct sleep command and recreate the pod
  $ kubectl create -f orange.yaml
  ```
 </details>

<br><br><br>

# Practice Test - OS Upgrades
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-os-upgrades/)
  
Solutions to practice test - OS Upgrades
- Let us explore the environment first. How many nodes do you see in the cluster?
  
  <details>
  ```
  $ kubectl get nodes
  ```
  </details>
  
- How many applications do you see hosted on the cluster?
  
  <details>
  ```
  $ kubectl get deploy
  ```
  </details>
  
- Run the command 'kubectl get pods -o wide' and get the list of nodes the pods are placed on
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- Run the command kubectl drain node01 --ignore-daemonsets
  
  <details>
  ```
  $ kubectl drain node01 --ignore-daemonsets
  ```
  </details>
  
- Run the command 'kubectl get pods -o wide' and get the list of nodes the pods are placed on
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- Run the command kubectl uncordon node01
  
  <details>
  ```
  $ kubectl uncordon node01
  ```
  </details>
  
- Run the command kubectl get pods -o wide
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- Why are there no pods on node01?
  
  <details>
  ```
  Only when new pods are created they will be scheduled
  ```
  </details>
  
- Use the command kubectl describe node master and look under taint section to check if it has any taints.
  
  <details>
  ```
  $ kubectl describe node master
  ```
  </details>
  
- Run the command kubectl drain node02 --ignore-daemonsets
  
  <details>
  ```
  $ kubectl drain node02 --ignore-daemonsets
  ```
  </details>
  
- Check the applications hosted on the node02.
  
  <details>
  ```
  node02 has a pod not part of a replicaset
  $ kubectl get pods -o wide
  ```
  </details>
  
- Check the list of pods
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
    
- What would happen to hr-app if node02 is drained forcefully?
  
  <details>
  ```
  $ kubectl drain node02 --ignore-daemonsets --force
  hr-app will be lost forever
  ```
  </details>
    
- Run the command kubectl drain node02 --ignore-daemonsets --force

  <details>
  ```
  $ kubectl drain node02 --ignore-daemonsets --force
  ```
  </details>
  
- Run the command kubectl cordon node03
  
  <details>
  ```
  $ kubectl cordon node03
  ```
  </details>

<br><br><br>

# Practice Test - Cluster Upgrade Process
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-cluster-upgrade-process/)
  
Solutions to practice test cluster upgrade process
- What is the current version of the cluster?
  
  <details>
  ```
  $ kubectl get nodes
  ```
  </details>
  
- How many nodes are part of this cluster?
  
  <details>
  ```
  $ kubctl get nodes
  ```
  </details>
  
- Check what nodes the pods are hosted on.
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- Count the number of deployments
  
  <details>
  ```
  $ kubectl get deploy
  ```
  </details>
  
- Run the command kubectl get pods -o wide
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- You are tasked to upgrade the cluster. User's accessing the applications must not be impacted. And you cannot provision new VMs. What strategy would you use to upgrade the cluster?
  
  <details>
  ```
  Upgrade one node at a time while moving the workloads to the other
  ```
  </details>
  
- Run the kubeadm upgrade plan command
  
  <details>
  ```
  $ kubeadm upgrade plan
  ```
  </details>
  
- Run the kubectl drain master --ignore-daemonsets
  
  <details>
  ```
  $ kubectl drain master --ignore-daemonsets
  ```
  </details>
  
- Run the command apt install kubeadm=1.18.0-00 and then kubeadm upgrade apply v1.18.0 and then apt install kubelet=1.18.0-00 to upgrade the kubelet on the master node
  
  <details>
  ```
  $ apt install kubeadm=1.18.0-00
  $ kubeadm upgrade apply v1.18.0 
  $ apt install kubelet=1.18.0-00
  ```
  </details>
  
- Run the command kubectl uncordon master
  
  <details>
  ```
  $ kubectl uncordon master 
  ```
  </details>
  
- Run the command kubectl drain node01 --ignore-daemonsets
  
  <details>
  ```
  $ kubectl drain node01 --ignore-daemonsets
  ```
  </details>
  
- Run the commands: apt install kubeadm=1.18.0-00 and then kubeadm upgrade node. Finally, run apt install kubelet=1.18.0-00.
  
  <details>
  ```
  $ apt install kubeadm=1.18.0-00
  $ kubeadm upgrade node
  $ apt install kubelet=1.18.0-00
  ```
  </details>
  
- Run the command kubectl uncordon node01
  
  <details>
  ```
  $ kubectl uncordon node01
  ```
  </details>

<br><br><br>

# Practice Test - Backup and Restore Methods
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-backup-and-restore-methods/)
  
Solutions to practice test - Backup and Restore Methods
- Run the kubectl get deployments command
  
  <details>
  ```
  $ kubectl get deployments
  ```
  </details>
  
- Look at the ETCD Logs using command kubectl logs etcd-master -n kube-system or check the ETCD pod kubectl describe pod etcd-master -n kube-system

  <details>
  ```
  $ kubectl logs etcd-master -n kube-system (or)
  $ kubectl describe pod etcd-master -n kube-system
  ```
  </details>
  
- Use the command kubectl describe pod etcd-master -n kube-system and look for --listen-client-urls
  
  <details>
  ```
  $ kubectl describe pod etcd-master -n kube-system 
  ```
  </details>
    
- Check the ETCD pod configuration kubectl describe pod etcd-master -n kube-system
  
  <details>
  ```
  $ kubectl describe pod etcd-master -n kube-system
  ```
  </details>
  
- Check the ETCD pod configuration kubectl describe pod etcd-master -n kube-system
  
  <details>
  ```
  $ kubectl describe pod etcd-master -n kube-system
  ```
  </details>
  
- Run the below command to backup etcd. View answer file at [etcd-backup-and-restore](https://github.com/mmumshad/kubernetes-the-hard-way/blob/master/practice-questions-answers/cluster-maintenance/backup-etcd/etcd-backup-and-restore.md)
  
  <details>
  ```
  $ ETCDCTL_API=3 etcdctl --endpoints=https://[127.0.0.1]:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt key=/etc/kubernetes/pki/etcd/server.key snapshot save /tmp/snapshot-pre-boot.db.
  ```
  </details>
  
- Wake up! We have a conference call! After the reboot the master nodes came back online, but none of our applications are accessible. Check the status of the applications on the cluster. What's wrong?
  
  <details>
  ```
  All of the above
  ```
  </details>
  
- Luckily we took a backup. Restore the original state of the cluster using the backup file. 
  - View answer file at [etcd-backup-and-restore](https://github.com/mmumshad/kubernetes-the-hard-way/blob/master/practice-questions-answers/cluster-maintenance/backup-etcd/etcd-backup-and-restore.md#3-restore-etcd-snapshot-to-a-new-folder)
  
  

#### Take me to [Solutions of Practice Tests - Backup and Restore](https://kodekloud.com/topic/solution-backup-and-restore/)

<br><br><br>

# Practice Test - View Certificates
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-view-certificate-details/)
  
Solutions to practice test - view certificates
- Identify the certificate file used for the kube-api server
  
  <details>
  
  ```
  $ cat /etc/kubernetes/manifest/kube-apiserver.yaml
  
  Answer: /etc/kubernetes/pki/apiserver.crt
  ```
  </details>
  
- Identify the Certificate file used to authenticate kube-apiserver as a client to ETCD Server
  
  <details>
  ```
  $ cat /etc/kubernetes/manifest/kube-apiserver.yaml
  Answer: /etc/kubernetes/pki/apiserver-etcd-client.crt
  ```
  </details>
  
- Look for kubelet-client-key option in the file /etc/kubernetes/manifests/kube-apiserver.yaml
  
  <details>
  ```
  Answer: /etc/kubernetes/pki/apiserver-kubelet-client.key
  ```
  </details>
  
- Look for cert file option in the file /etc/kubernetes/manifests/etcd.yaml
  
  <details>
  ```
  Answer: /etc/kubernetes/pki/etcd/server.crt
  ```
  </details>
  
- Look for CA Certificate in file /etc/kubernetes/manifests/etcd.yaml
  
  <details>
  ```
  Answer: /etc/kubernetes/pki/etcd/ca.crt
  ```
  </details>
  
- Run the command openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text
  
  <details>
  ```
  $ openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text
  ```
  </details>
  
- Run the command openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text and look for issuer
  
  <details>
  ```
  $ openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text 
  ```
  </details>
  
- Run the command openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text and look at Alternative Names
  
  <details>
  ```
  $ openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text
  ```
  </details>
  
- Run the command openssl x509 -in /etc/kubernetes/pki/etcd/server.crt -text and look for Subject CN.
  
  <details>
  ```
  $ openssl x509 -in /etc/kubernetes/pki/etcd/server.crt -text
  ```
  </details>
  
- Run the command openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text and check on the Expiry date.
  
  <details>
  ```
  $ openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text
  ```
  </details>
  
- Run the command 'openssl x509 -in /etc/kubernetes/pki/ca.crt -text' and look for validity
  
  <details>
  ```
  $ openssl x509 -in /etc/kubernetes/pki/ca.crt -text
  ```
  </details>
  
- Inspect the --cert-file option in the manifests file.
  
  <details>
  ```
  $ vi /etc/kubernetes/manifests/etcd.yaml
  ```
  </details>
  
- ETCD has its own CA. The right CA must be used for the ETCD-CA file in /etc/kubernetes/manifests/kube-apiserver.yaml. 
  
  <details>
  ```
  View answer at /var/answers/kube-apiserver.yaml
  ```
  </details>

<br><br><br>

# Practice Test - Certificates API
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-certificates-api/)

Solutions to the practice test - certificate API
- A new member akshay joined our team. He requires access to our cluster. The Certificate Signing Request is at the /root location.

  <details>
  ```
  $ ls -l /root
  ```
  </details>
  
- View the answer at /var/answers/akshay-csr.yaml
  
  <details>
  ```
  $ kubectl create -f /var/answers/akshay-csr.yaml
  ```
  </details>
  
- Run the command kubectl get csr
  
  <details>
  ```
  $ kubectl get csr
  ```
  </details>
    
- Run the command kubectl certificate approve akshay
  
  <details>
  ```
  $ kubectl certificate approve akshay
  ```
  </details>
  
- Run the command kubectl get csr
  
  <details>
  ```
  $ kubectl get csr
  ```
  </details>
  
- Run the command kubectl get csr and look at the Requestor column
  
  <details>
  ```
  $ kubectl get csr
  ```
  </details>
  
- The other CSR's are requested during the TLS Bootstrapping process. We will discuss more about it later in the course when we go through the TLS bootstrap section.

- Run the command kubectl get csr
  
  <details>
  ```
  $ kubectl get csr
  ```
  </details>
  
- Run the command kubectl get csr agent-smith -o yaml
  
  <details>
  ```
  $ kubectl get csr agent-smith -o yaml
  ```
  </details>
  
- Run the command kubectl certificate deny agent-smith
  
  <details>
  ```
  $ kubectl certificate deny agent-smith
  ```
  </details>
  
- Run the command kubectl delete csr agent-smith
  
  <details>
  ```
  $ kubectl delete csr agent-smith
  ```
  </details>

<br><br><br>

# Practice Test - KubeConfig
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-kubeconfig/)
 
Solutions to the practice test - kubeconfig
- Look for the kube config file under `/root/.kube`
  
  <details>
  ```
  $ ls -l /root/.kube
  ```
  </details>
    
- Run the kubectl config view command and count the number of clusters

  <details>
  ```
  $ kubectl config view
  ```
  </details>
    
- Run the command `kubectl config view` and count the number of users

  <details>
  ```
  $ kubectl config view
  ```
  </details>
  
- How many contexts are defined in the default kubeconfig file?
  
  <details>
  ```
  $ kubectl config view
  ```
  </details>
  
- Run the command 'kubectl config view' and look for the user name.
  
  <details>
  ```
  $ kubectl config view
  ```
  </details>
  
- What is the name of the cluster configured in the default kubeconfig file?
  
  <details>
  ```
  $ kubectl config view
  ```
  </details>
  
- Run the command 'kubectl config view --kubeconfig my-kube-config'
  
  <details>
  ```
  $ kubectl config view --kubeconfig my-kube-config
  ```
  </details>
  
- How many contexts are configured in the 'my-kube-config' file?
  
  <details>
  ```
  $ kubectl config view --kubeconfig my-kube-config
  ```
  </details>
  
- What user is configured in the 'research' context?
  
  <details>
  ```
  $ kubectl config view --kubeconfig my-kube-config
  ```
  </details>
    
- What is the name of the client-certificate file configured for the 'aws-user'?
  
  <details>
  ```
  $ kubectl config view --kubeconfig my-kube-config
  ```
  </details>
  
- What is the current context set to in the 'my-kube-config' file?
  
  <details>
  ```
  $ kubectl config view --kubeconfig my-kube-config
  ```
  </details>
  
- Run the command kubectl config --kubeconfig=/root/my-kube-config use-context research
  
  <details>
  ```
  $ kubectl config --kubeconfig=/root/my-kube-config use-context research
  ```
  </details>
  
- Replace the contents in the default kubeconfig file with the content from my-kube-config file.
  
  <details>
  ```
  $ mv .kube/config .kube/config.bak
  $ cp /root/my-kube-config .kube/config
  ```
  </details>
  
- The path to certificate is incorrect in the kubeconfig file. Fix it. All users certificates are stored at /etc/kubernetes/pki/users
  
 <details>
  $ kubectl get pods
  master $ ls
  dev-user.crt  dev-user.csr  dev-user.key
  master $ vi /root/.kube/config
  master $ grep dev-user.crt /root/.kube/config
    client-certificate: /etc/kubernetes/pki/users/dev-user/dev-user.crt
  master $ pwd
  /etc/kubernetes/pki/users/dev-user
  master $ kubectl get pods
  No resources found in default namespace.
 </details>

<br><br><br>

# Practice Test - RBAC
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-role-based-access-controls/)

Solutions to practice test - RBAC
- Run the command kubectl describe pod kube-apiserver-master -n kube-system and look for --authorization-mode
  
  <details>
  
  ```
  $ kubectl describe pod kube-apiserver-master -n kube-system
  ```
  
  </details>
  
- Run the command kubectl get roles

  <details>
  
  ```
  $ kubectl get roles
  ```
  
  </details>
  
- Run the command kubectl get roles --all-namespaces
  
  <details>
  
  ```
  $ kubectl get roles --all-namespaces
  ```
  
  </details>
  
- Run the command kubectl describe role kube-proxy -n kube-system
  
  <details>
  
  ```
  $ kubectl describe role kube-proxy -n kube-system
  ```
  
  </details>
  
- Check the verbs associated to the kube-proxy role
  
  <details>
  ```
  $ kubectl describe role kube-proxy -n kube-system
  ```
  </details>
  
- Which of the following statements are true?
  
  <details>
  ```
  kube-proxy role can get details of configmap object by the name kube-proxy
  ```
  </details>
  
- Run the command kubectl describe rolebinding kube-proxy -n kube-system
  
  <details>
  ```
  $ kubectl describe rolebinding kube-proxy -n kube-system
  ```
  </details>
  
- Run the command kubectl get pods --as dev-user
  
  <details>
  ```
  $ kubectl get pods --as dev-user
  ```
  </details>
  
- Answer file located at /var/answers
  
  <details>
  
  ```
  $ kubectl create -f /var/answers/developer-role.yaml
  ```
  
  </details>
  
- New roles and role bindings are created in the blue namespace. Check it out. Check the resourceNames configured on the role
  
  <details>
  
  ```
  $ kubectl get roles,rolebindings -n blue
  $ kubectl describe role developer -n blue
  $ kubectl edit role developer -n blue (update the resourceNames)
  ```
  
  </details>
  
- View the answer file located at /var/answers/dev-user-deploy.yaml
  
  <details>
  
  ```
  $ kubectl create -f /var/answers/dev-user-deploy.yaml
  ```
  
  </details>

<br><br><br>

# Practice Test - Cluster Roles
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-cluster-roles/)
 
Solutions to practice test - cluster roles
- Run the command kubectl get clusterroles --no-headers | wc -l or kubectl get clusterroles --no-headers -o json | jq '.items | length'
  
  <details>
  
  ```
  $ kubectl get clusterroles --no-headers | wc -l (or)
  $ kubectl get clusterroles --no-headers -o json | jq '.items | length'
  ```
  
  </details>
  
- Run the command kubectl get clusterrolebindings --no-headers | wc -l or kubectl get clusterrolebindings --no-headers -o json | jq '.items | length'

  <details>
  
  ```
  $ kubectl get clusterrolebindings --no-headers | wc -l (or)
  $ kubectl get clusterrolebindings --no-headers -o json | jq '.items | length'
  ```
  
  </details>
  
- What namespace is the cluster-admin clusterrole part of?

  <details>
  
  ```
  $ Cluster roles are cluster wide and not part of any namespace
  ```
  
  </details>
  
- Run the command kubectl describe clusterrolebinding cluster-admin
  
  <details>
  
  ```
  $ kubectl describe clusterrolebinding cluster-admin
  ```
  
  </details>
  
- Run the command kubectl describe clusterrole cluster-admin

  <details>
  
  ```
  $ kubectl describe clusterrole cluster-admin
  ```
  
  </details>
  
- Check answer at /var/answers

  <details>
  
  ```
  $ kubectl create -f /var/answers/michelle-node-admin.yaml
  ```
  
  </details>
  
- Check answer at /var/answers

  <details>
  
  ```
  $ kubectl create -f /var/answers/michelle-storage-admin.yaml
  ```
  
  </details>
  
<br><br><br>

# Practice Test - Image Security
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-image-security/)

Solutions to the practice test - Image Security
- We have an application running on our cluster. Let us explore it first. What image is the application using?

  <details>
  
  ```
  $ kubectl get deploy -o wide
  ```
  
  </details>
  
- Use the kubectl edit deployment command to edit the image name to myprivateregistry.com:5000/nginx:alpine

  <details>
  
  ```
  $ kubectl edit deployment web
  ```
  
  </details>
  
- Run the command kubectl get pods command and check the status of the pods

  <details>
  
  ```
  $ kubectl get pods
  ```
  
  </details>
  
- Run command kubectl create secret docker-registry private-reg-cred --docker-username=dock_user --docker-password=dock_password --docker-server=myprivateregistry.com:5000 --docker-email=dock_user@myprivateregistry.com
  
  <details>
  
  ```
  $ kubectl create secret docker-registry private-reg-cred --docker-username=dock_user --docker-password=dock_password --docker-server=myprivateregistry.com:5000 --docker-email=dock_user@myprivateregistry.com
  ```
  
  </details>
  
- Edit deployment using kubectl edit deploy web command and add imagePullSecrets section. Use private-reg-cred
  
  <details>
  
  ```
  $ kubectl edit deploy web
  ```
  
  </details>
  
- Check the status of PODs. Wait for them to be running. You have now successfully configured a Deployment to pull images from the private registry
  
  <details>
  
  ```
  $ kubectl get pods
  ```
  </details>

  <br><br><br>

# Practice Test - Security Context
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-security-contexts/)
  
Solutions to practice test - security context
- Run the command 'kubectl exec ubuntu-sleeper whoami' and count the number of pods.

  <details>
  
  ```
  $ kubectl exec ubuntu-sleeper whoami
  ```
  
  </details>
  
- Set a security context to run as user 1010.

  <details>
  
  ```
  $ kubectl get pods ubuntu-sleeper -o yaml > ubuntu.yaml
  $ kubectl delete pod ubuntu-sleeper
  $ vi ubuntu.yaml ( add securityContext Section)
    securityContext:
      runAsUser: 1010
  $ kubectl create -f ubuntu.yaml
  ```
  
  </details>
  
- The User ID defined in the securityContext of the container overrides the User ID in the POD.
 
- The User ID defined in the securityContext of the POD is carried over to all the PODs in the container.

- Run kubectl exec -it ubuntu-sleeper -- date -s '19 APR 2012 11:14:00'
  
  <details>
  
  ```
  $ kubectl exec -it ubuntu-sleeper -- date -s '19 APR 2012 11:14:00'
  ```
  
  </details>
  
- Add SYS_TIME capability to the container's securityContext
  
  <details>
  
  ```
  $ kubectl get pods ubuntu-sleeper -o yaml > ubuntu.yaml
  $ kubectl delete pod ubuntu-sleeper
  $ vi ubuntu.yaml
  
  Under container section add the below
  
  securityContext:
      capabilities:
        add: ["SYS_TIME"]
        
  $ kubectl create -f ubuntu.yaml
  ```
  
  </details>
  
 - Now try to run the below command in the pod to set the date. If the security capability was added correctly, it should work. If it doesn't make sure you changed the user back to root.
  
   <details>
  
   ```
   $ kubectl exec -it ubuntu-sleeper -- date -s '19 APR 2012 11:14:00'
   ```
  
   </details>

<br><br><br>

# Practice Test - Network Policies
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-network-policies/)

Solutions to practice test - network policies

- Run the command 'kubectl get networkpolicy'
  
  <details>
  
  ```
  $ kubectl get networkpolicy
  ```
  
  </details>
  
- Run the command 'kubectl get networkpolicy'
   
  <details>
  
  ```
  $ kubectl get networkpolicy
  ```
  
  </details>
  
- Run the command 'kubectl get networkpolicy' and look under pod selector
  
  <details>
  
  ```
  $ kubectl get networkpolicy
  ```
  
  </details>
  
- Run the command 'kubectl describe networkpolicy' and look under PolicyTypes
  
  <details>
  
  ```
  $ kubectl describe networkpolicy
  ```
  
  </details>
  
- What is the impact of the rule configured on this Network Policy?
  
  <details>
  
  ```
  Traffic from internal to payroll pod is blocked
  ```
  
  </details>
  
- What is the impact of the rule configured on this Network Policy?
  
  <details>
  
  ```
  Internal pod can access port 8080 on payroll pod
  ```
  
  </details>
  
- Access the UI of these applications using the link given above the terminal.

- Only internal applications can access payroll service

- Perform a connectivity test using the User Interface of the Internal Application to access the 'external-service' at port '8080'.
  
  <details>
  
  ```
  Successful
  ```
  
  </details>
  
- Answer file located at /var/answers/answer-internal-policy.yaml
  
  <details>
  
  ```
  $ kubectl create -f /var/answers/answer-internal-policy.yaml
  ```
  
  </details>
  
<br><br><br>

# Practice Test - Persistent Volume Claims

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-persistent-volume-claims/)

#### Solution

  1. Check the Solution

     <details>

      ```
      OK
      ```
    
     </details>

  2. Check the Solution

     <details>

      ```
      OK
      ```
     </details>
 
  3. Check the Solution

     <details>

      ```
      No
      ```
     </details>

  4. Check the Solution
    
     <details>

      ```
      apiVersion: v1
      kind: Pod
      metadata:
        name: webapp
      spec:
        containers:
        - name: event-simulator
          image: kodekloud/event-simulator
          env:
          - name: LOG_HANDLERS
            value: file
          volumeMounts:
          - mountPath: /log
            name: log-volume
      
        volumes:
        - name: log-volume
          hostPath:
            # directory location on host
            path: /var/log/webapp
            # this field is optional
            type: Directory
      ```
      </details>

  5. Check the Solution

     <details>

      ```
      apiVersion: v1
      kind: PersistentVolume
      metadata:
        name: pv-log
      spec:
        accessModes:
          - ReadWriteMany
        capacity:
          storage: 100Mi
        hostPath:
          path: /pv/log
      ```

     </details>

  6. Check the Solution

     <details>

      ```
      kind: PersistentVolumeClaim
      apiVersion: v1
      metadata:
        name: claim-log-1
      spec:
        accessModes:
          - ReadWriteOnce
        resources:
          requests:
            storage: 50Mi
      ```
     </details>

  7. Check the Solution

     <details>

      ```
      PENDING
      ```
     </details>

  8. Check the Solution

     <details>

      ```
      AVAILABLE
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      Access Modes Mismatch
      ```
     </details>

  10. Check the Solution

      <details>
 
       ```
       kind: PersistentVolumeClaim
       apiVersion: v1
       metadata:
         name: claim-log-1
       spec:
         accessModes:
           - ReadWriteMany
         resources:
           requests:
             storage: 50Mi
       ```
      </details>

  11. Check the Solution

      <details>
 
       ```
       100Mi
       ```
      </details>

  12. Check the Solution

      <details>
 
       ```
       apiVersion: v1
       kind: Pod
       metadata:
         name: webapp
       spec:
         containers:
         - name: event-simulator
           image: kodekloud/event-simulator
           env:
           - name: LOG_HANDLERS
             value: file
           volumeMounts:
           - mountPath: /log
             name: log-volume
       
         volumes:
         - name: log-volume
           persistentVolumeClaim:
             claimName: claim-log-1
       ```
      </details>

  13. Check the Solution

      <details>
 
       ```
       Retain
       ```
      </details>

  14. Check the Solution

      <details>
 
       ```
       The PV is not delete but not available
       ```
      </details>

  15. Check the Solution

      <details>
 
       ```
       The PVC is stuck in `terminating` state
       ```
      </details>

  16. Check the Solution

      <details>
 
       ```
       The PVC is being used by a POD
       ```
      </details>

  17. Check the Solution

      <details>
 
       ```
       kubectl delete pod webapp
       ```
      </details>

  18. Check the Solution

      <details>
 
       ```
       Deleted
       ```
      </details>

  19. Check the Solution

      <details>
 
       ```
       Released
       ```
      </details>

<br><br><br>

# Practice Test - Storage Class
  
  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-storage-class-2/)

#### Solution

  1. Check the Solution

     <details>

      ```
      0
      ```
    
     </details>

  2. Check the Solution

     <details>

      ```
      2
      ```
     </details>
 
  3. Check the Solution

     <details>

      ```
      local-storage
      ```
     </details>

  4. Check the Solution
    
     <details>

      ```
      WaitForFirstConsumer
      ```
      </details>

  5. Check the Solution

     <details>

      ```
      portworx-volume
      ```

     </details>

  6. Check the Solution

     <details>

      ```
      NO
      ```
     </details>

  7. Check the Solution

     <details>

      ```
      apiVersion: v1
      kind: PersistentVolumeClaim
      metadata:
        name: local-pvc
      spec:
        accessModes:
        - ReadWriteOnce
        resources:
          requests:
            storage: 500Mi
        storageClassName: local-storage
      ```
     </details>

  8. Check the Solution

     <details>

      ```
      Pending
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      A Pod consuming the volume in not scheduled
      ```
     </details>

  10. Check the Solution

      <details>
 
       ```
       The Storage Class called local-storage makes use of VolumeBindingMode set to WaitForFirstConsumer. This will delay the binding and provisioning of a PersistentVolume until a Pod using the PersistentVolumeClaim is created.
       ```
      </details>

  11. Check the Solution

      <details>
 
       ```
       apiVersion: v1
       kind: Pod
       metadata:
         name: nginx
         labels:
           name: nginx
       spec:
           containers:
           - name: nginx
             image: nginx:alpine
             volumeMounts:
             - name: local-persistent-storage
               mountPath: /var/www/html
           volumes:
           - name: local-persistent-storage
             persistentVolumeClaim:
               claimName: local-pvc
       ```
      </details>

  12. Check the Solution

      <details>
 
       ```
       apiVersion: storage.k8s.io/v1
       kind: StorageClass
       metadata:
         name: delayed-volume-sc
       provisioner: kubernetes.io/no-provisioner
       volumeBindingMode: WaitForFirstConsumer
       ```
      </details>

<br><br><br>

# Practice Test - Explore Env

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-explore-environment/)

#### Solution

  1. Check the Solution

     <details>

      ```
       2 
      ```
     </details>

  2. Check the Solution

     <details>

      ```
      ens3
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      172.17.0.31
      ```
     </details>

  4. Check the Solution

     <details>

      ```
      02:42:ac:11:00:1f
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      172.17.0.32
      ```
     </details>

  6. Check the Solution

     <details>

      ```
      02:42:ac:11:00:20
      ```
     </details>

  7. Check the Solution

     <details>

      ```
      docker0
      ```
     </details>

  8. Check the Solution

     <details>

      ```
      DOWN
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      172.17.0.1
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      10251
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      2379
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      Ok
      ```
     </details>

<br><br><br>

# Practice Test - CNI weave

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-cni-weave/)

#### Solution

  1. Check the Solution

     <details>

      ``` 
      CNI
      ```
     </details>

  2. Check the Solution

     <details>

      ```
      /opt/cni/bin
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      cisco
      ```
     </details>

  4. Check the Solution

     <details>

      ```   
      weave
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      weave-net
      ```
     </details>

<br><br><br>

# Practice Test - Deploy Networking Solution

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-deploy-network-solution/)

#### Solution

  1. Check the Solution

     <details>

      ```
      Not Running
      ```
     </details>

  2. Check the Solution

     <details>

      ```
      No Network Configured
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      Click [here](https://www.weave.works/docs/net/latest/kubernetes/kube-addon/)

      OR Execute below command

      kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
      ```
     </details>

<br><br><br>

# Practice Test Networking Weave

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-networking-weave/)

#### Solution 

  1. Check the Solution

     <details>

      ```
      4
      ```
     </details>

  2. Check the Solution

     <details>

      ```
      weave
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      4
      ```
     </details>

  4. Check the Solution

     <details>

      ```
      One on every node
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      weave
      ```
     </details>

  6. Check the Solution

     <details>

      ```
      10.X.X.X
      ```
     </details>

  7. Check the Solution

     <details>

      ```
      10.38.0.0
      ```
     </details>

<br><br><br>

# Practice Test Service Networking

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-service-networking/)

#### Solution 

  1. Check the Solution

     <details>

      ```
      172.17.0.0/16
      ```
     </details>

  2. Check the Solution

     <details>

      ```
      10.32.0.0/12
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      10.96.0.0/12
      ```
     </details>

  4. Check the Solution

     <details>

      ```
      2
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      iptables
      ```
     </details>

  6. Check the Solution

     <details>

      ```
      using daemonset
      ```
     </details>

<br><br><br>

# Practice Test CoreDNS in Kubernetes

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-coredns-in-kubernetes/)

#### Solution 

  1. Check the Solution

     <details>

      ```
      CoreDNS
      ```
     </details>
  
  2. Check the Solution

     <details>

      ```
      2
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      10.96.0.10
      ```
     </details>

  4. Check the Solution

     <details>

      ```
      /etc/coredns/Corefile

      OR

      kubectl -n kube-system describe deployments.apps coredns | grep -A2 Args | grep Corefile
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      Configured as a ConfigMapObject
      ```
     </details>

  6. Check the Solution

     <details>

      ```
      CoreDNS
      ```
     </details>

  7. Check the Solution

     <details>

      ```
      coredns
      ```
     </details>

  8. Check the Solution

     <details>

      ```
      cluster.local
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      Ok
      ```
     </details>

  10. Check the Solution

      <details>

       ```
       web-service
       ```
      </details>

  11. Check the Solution

      <details>
 
       ```
       web-serivce.default.pod
       ```
      </details>

  12. Check the Solution

      <details>
 
       ```
       web-service.payroll
       ```
      </details>

  13. Check the Solution

      <details>
 
       ```
       web-service.payroll.svc.cluster
       ```
      </details>

  14. Check the Solution

      <details>
 
       ```
       kubectl edit deploy webapp
 
       Search for DB_Host and Change the DB_Host from mysql to mysql.payroll
 
       spec:
         containers:
         - env:
           - name: DB_Host
             value: mysql.payroll
       ```
      </details>
 
  15. Check the Solution

      <details>
 
       ```
       kubectl exec -it hr -- nslookup mysql.payroll > /root/nslookup.out
       ```
      </details>

<br><br><br>

# Practice Test CKA Ingress 1

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-cka-ingress-networking-1/)

#### Solution 

  1. Check the Solution

     <details>

      ```
      Ok
      ```
     </details>
  
  2. Check the Solution

     <details>

      ```
      INGRESS-SPACE
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      NGINX-INGRESS-CONTROLLER
      ```
     </details>

  4. Check the Solution

     <details>

      ```
      APP-SPACE
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      3
      ```
     </details>

  6. Check the Solution

     <details>

      ```
      APP-SPACE
      ```
     </details>

  7. Check the Solution

     <details>

      ```
      INGRESS-WEAR-WATCH
      ```
     </details>

  8. Check the Solution

     <details>

      ```
      ALL-HOSTS(*)
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      WEAR-SERVICE
      ```
     </details>

  10. Check the Solution

      <details>

       ```
        /WATCH
       ```
      </details>

  11. Check the Solution

      <details>

       ```
        DEFAULT-HTTP-BACKEND
       ```
      </details>

  12. Check the Solution

      <details>

       ```
        404-ERROR-PAGE
       ```
      </details>

  13. Check the Solution

      <details>

       ```
        OK
       ```
      </details>

  14. Check the Solution

      <details>
 
        ```
        kubectl edit ingress --namespace app-space
 
        Change the path from /watch to /stream
    
        OR
 
        apiVersion: v1
        items:
        - apiVersion: extensions/v1beta1
          kind: Ingress
          metadata:
            annotations:
              nginx.ingress.kubernetes.io/rewrite-target: /
              nginx.ingress.kubernetes.io/ssl-redirect: "false"
            name: ingress-wear-watch
            namespace: app-space
          spec:
            rules:
            - http:
                paths:
                - backend:
                    serviceName: wear-service
                    servicePort: 8080
                  path: /wear
                  pathType: ImplementationSpecific
                - backend:
                    serviceName: video-service
                    servicePort: 8080
                  path: /stream
                  pathType: ImplementationSpecific
          status:
            loadBalancer:
              ingress:
              - {}
        kind: List
        metadata:
          resourceVersion: ""
          selfLink: ""
       ```
      </details>

  15. Check the Solution

      <details>

       ```
        OK
       ```
      </details>

  16. Check the Solution

      <details>

       ```
        404 ERROR PAGE
       ```
      </details>

  17. Check the Solution

      <details>

       ```
        OK
       ```
      </details>

  18. Check the Solution

      <details>

       ```
        Run the command 'kubectl edit ingress --namespace app-space' and add a new Path entry for the new service.

        OR

       apiVersion: v1
       items:
       - apiVersion: extensions/v1beta1
         kind: Ingress
         metadata:
           annotations:
             nginx.ingress.kubernetes.io/rewrite-target: /
             nginx.ingress.kubernetes.io/ssl-redirect: "false"
           name: ingress-wear-watch
           namespace: app-space
         spec:
           rules:
           - http:
               paths:
               - backend:
                   serviceName: wear-service
                   servicePort: 8080
                 path: /wear
                 pathType: ImplementationSpecific
               - backend:
                   serviceName: video-service
                   servicePort: 8080
                 path: /stream
                 pathType: ImplementationSpecific
               - backend:
                   serviceName: food-service
                   servicePort: 8080
                 path: /eat
                 pathType: ImplementationSpecific
         status:
           loadBalancer:
             ingress:
             - {}
       kind: List
       metadata:
         resourceVersion: ""
         selfLink: ""
       ```
      </details>

  19. Check the Solution

      <details>

       ```
        OK
       ```
      </details>

  20. Check the Solution

      <details>

       ```
        CRITICAL-SPACE
       ```
      </details>

  21. Check the Solution

      <details>

       ```
        WEBAPP-PAY
       ```
      </details>

  22. Check the Solution

      <details>

       ```
        apiVersion: extensions/v1beta1
        kind: Ingress
        metadata:
          name: test-ingress
          namespace: critical-space
          annotations:
            nginx.ingress.kubernetes.io/rewrite-target: /
        spec:
          rules:
          - http:
              paths:
              - path: /pay
                backend:
                  serviceName: pay-service
                  servicePort: 8282
        ```
        </details>

  23. Check the Solution

      <details>

       ```
        OK
       ```
      </details>

<br><br><br>

# Practice Test CKA Ingress 2

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-cka-ingress-networking-2/)

#### Solution 

  1. Check the Solution

     <details>

      ```
      OK
      ```
     </details>

  2. Check the Solution

     <details>

      ```
      kubectl create namespace ingress-space
      ```
     </details>

  3. Check the Solution

     <details>

      ```
      kubectl create configmap nginx-configuration --namespace ingress-space
      ```
     </details>

  4. Check the Solution

     <details>

      ```
      kubectl create serviceaccount ingress-serviceaccount --namespace ingress-space
      ```
     </details>

  5. Check the Solution

     <details>

      ```
      Ok

      kubectl get roles,rolebindings --namespace ingress-space
      ```
     </details>

  6. Check the Solution

     <details>

      ```
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        name: ingress-controller
        namespace: ingress-space
      spec:
        replicas: 1
        selector:
          matchLabels:
            name: nginx-ingress
        template:
          metadata:
            labels:
              name: nginx-ingress
          spec:
            serviceAccountName: ingress-serviceaccount
            containers:
              - name: nginx-ingress-controller
                image: quay.io/kubernetes-ingress-controller/nginx-ingress-controller:0.21.0
                args:
                  - /nginx-ingress-controller
                  - --configmap=$(POD_NAMESPACE)/nginx-configuration
                  - --default-backend-service=app-space/default-http-backend
                env:
                  - name: POD_NAME
                    valueFrom:
                      fieldRef:
                        fieldPath: metadata.name
                  - name: POD_NAMESPACE
                    valueFrom:
                      fieldRef:
                        fieldPath: metadata.namespace
                ports:
                  - name: http
                    containerPort: 80
                  - name: https
                    containerPort: 443
      ```
     </details>
  
  7. Check the Solution

     <details>

      ```
      apiVersion: v1
      kind: Service
      metadata:
        name: ingress
        namespace: ingress-space
      spec:
        type: NodePort
        ports:
        - port: 80
          targetPort: 80
          protocol: TCP
          nodePort: 30080
          name: http
        - port: 443
          targetPort: 443
          protocol: TCP
          name: https
        selector:
          name: nginx-ingress
      ```
     </details>

  8. Check the Solution

     <details>

      ```
      apiVersion: extensions/v1beta1
      kind: Ingress
      metadata:
        name: ingress-wear-watch
        namespace: app-space
        annotations:
          nginx.ingress.kubernetes.io/rewrite-target: /
          nginx.ingress.kubernetes.io/ssl-redirect: "false"
      spec:
        rules:
        - http:
            paths:
            - path: /wear
              backend:
                serviceName: wear-service
                servicePort: 8080
            - path: /watch
              backend:
                serviceName: video-service
                servicePort: 8080
      ```
     </details>

  9. Check the Solution

     <details>

      ```
      OK
      ```
     </details>

<br><br><br>

# Practice Test - Install kubernetes cluster using kubeadm tool

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-deploy-a-kubernetes-cluster-using-kubeadm/)

# Solutions for practice test - Install Using Kubeadm

  1. Check the solution

     <details>
     
      ```
      sudo apt-get update && sudo apt-get install -y apt-transport-https curl
      curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
      cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
      deb https://apt.kubernetes.io/ kubernetes-xenial main
      EOF
      sudo apt-get update
      sudo apt-get install -y kubelet kubeadm kubectl
      sudo apt-mark hold kubelet kubeadm kubectl
      ```
     </details>

  2. Check the solution

     <details>
      
      ```
      kubelet --version
      ``` 
     </details>

  3. Check the solution

     <details>
      
      ```
      0
      ``` 
     </details>

  5. Click on **`OK`**

  6. Check the solution

     <details>
      
      ```
      kubeadm init
      ``` 
     </details>

  7. Click on **`OK`**

  8. Click on **`Check`** 

  9. Check the solution

     <details>

      ```
      kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
      ```
     </details>

<br><br><br>

# Practice Test - Application Failure

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-application-failure/) of the Application Failure

    ### Solution

    1. Check Solution 

       <details>

        ```
         kubectl delete svc mysql -n alpha
        ```
        
        ```
         apiVersion: v1
         kind: Service
         metadata:
           name: mysql-service
           namespace: alpha
         spec:
           ports:
           - port: 3306
             protocol: TCP
             targetPort: 3306
           selector:
             name: mysql
           sessionAffinity: None
           type: ClusterIP
         status:
           loadBalancer: {}
        ```   
       </details>

    2. Check Solution

       <details>
  
       You can edit the `mysql-service` service and change the targetPort "8080" to "3306".
        ```
        kubectl edit svc mysql-service -n beta
        ```
        
       OR
        
       Delete the `mysql-service` service and then apply below manifest:
        ```
        kubectl delete svc mysql-service -n beta
        ```
  
        ```
        apiVersion: v1
        kind: Service
        metadata:
          name: mysql-service
          namespace: beta
        spec:
          ports:
          - port: 3306
            protocol: TCP
            targetPort: 3306
          selector:
            name: mysql
          sessionAffinity: None
          type: ClusterIP
        status:
          loadBalancer: {}
        ```
       </details>

    3. Check Solution

       <details>

       ```
       kubectl edit svc mysql-service -n gamma
       Press Esc, then colon(:)
       :%s/sql00001/mysql/
       ```
       </details>

    4. Check Solution

       <details>

        ```
        kubectl edit deployment.apps/webapp-mysql -n delta

        Change the DB_User's value to root.

        :%s/sql-user/root

        - name: DB_User
          value: root
        ```
       </details>

    5. Check Solution

       <details>
 
        ```
        kubectl edit pod mysql -n epsilon

        Replace the DB_Password with the correct password as shown below, then delete the pod and re-create it again.
        
        :%s/passwooooorrddd/paswrd
        
        save the file with ":wq" in vi editor and it will create a temporary file with random name under the default path /tmp/kubectl-edit-xxxxx.yaml. After deleting the existing one, re-create it again with kubectl apply -f or kubectl create -f command.
        
        In the "webapp-mysql" deployments, change the DB_User's value to root.
        
        kubectl edit deployment.apps/webapp-mysql -n epsilon

        :%s/sql-user/root

        - name: DB_User
          value: root
          
        save the file and exit with ":wq" in vi editor. 
        ```
       </details>
    
    6. Check Solution

       <details>
 
        ```
        kubectl edit deployment.apps/webapp-mysql -n zeta

        Change the DB_User's value to root.

        :%s/sql-user/root

        - name: DB_User
          value: root
        ```

        ```
        Replace the DB_Password with the correct password as shown below, delete the pod and re-create it.

        kubectl edit pod mysql -n zeta

        :%s/passwooooorrddd/paswrd
     
        save the file with ":wq" in vi editor and it will create a temporary file with random name under the default path /tmp/kubectl-edit-xxxxx.yaml. After deleting the existing one, re-create it again with kubectl apply -f or kubectl create -f command. 
        ```

        ```
        kubectl edit svc web-service -n zeta

        Change the nodePort from "30088" to "30081".

        :%s/30088/30081
        ```
       </details>

<br><br><br>

# Solution Control Plane Failure

  - Lets have a look at the [Practice Test](https://kodekloud.com/topic/practice-test-control-plane-failure/) of the Control Plane Failure

    ### Solution

    1. Check Solution 

       <details>

        ```
        kubectl get pods -n kube-system
        ```

        ```
        sed -i 's/kube-schedulerrrr/kube-scheduler/g' /etc/kubernetes/manifests/kube-scheduler.yaml
        ```
       </details>

    2. Check Solution

       <details>

        ```
        kubectl scale deploy app --replicas=2
        ```
       </details>

    3. Check Solution

       <details>

        ```
        sed -i 's/controller-manager-XXXX.conf/controller-manager.conf/' /etc/kubernetes/manifests/kube-controller-manager.yaml
        ```
       </details>

    4. Check Solution

       <details>

        ```
        sed -i 's/WRONG-PKI-DIRECTORY/pki/' /etc/kubernetes/manifests/kube-controller-manager.yaml
        ```
       </details>

<br><br><br>

# Solution Worker Node Failure

  - Lets have a look at the [Practice Test](https://kodekloud.com/topic/practice-test-worker-node-failure/) of the Worker Node Failure

    ### Solution

    1. Check Solution 

       <details>

        ```
        ssh node01

        service kubelet start
        ```
        </details>

    2. Check Solution
      
       <details>

        ```
        sed -i 's/WRONG-CA-FILE.crt/ca.crt/g' /var/lib/kubelet/config.yaml
        ```
       </details>

    3. Check Solution
      
       <details>

        ```
        sed -i 's/6553/6443/g' /etc/kubernetes/kubelet.conf
        ```
       </details>

<br><br><br>

# Solution Troubleshoot Network

  - Lets have a look at the [Practice Test](https://kodekloud.com/topic/practice-test-troubleshoot-network/) of the Troubleshoot Network

    ### Solution

    1. Check Solution

       <details>

        ```
         The pods are in a pending state? Does the cluster have a Network Addon installed?
		 Install Weave using:
		 kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
        ```
        </details>

    2. Check Solution

       <details>

        ```
         The kube-proxy pods are not running. As a result the rules needed to allow connectivity to the services have not been created.

         1. Check the logs of the kube-proxy pods
         kubectl -n kube-system logs <name_of_the_kube_proxy_pod>

         2. The configuration file "/var/lib/kube-proxy/configuration.conf" is not valid. The configuration path does not match the data in the ConfigMap.
         kubectl -n kube-system describe configmap kube-proxy shows that the file name used is "config.conf" which is mounted in the kube-proxy daemonset pods at the path /var/lib/kube-proxy/config.conf

         3. However in the DaemonSet for kube-proxy, the command used to start the kube-proxy pod makes use of the path /var/lib/kube-proxy/configuration.conf.

          Correct this path to /var/lib/kube-proxy/config.conf as per the ConfigMap and recreate the kube-proxy pods.

          This should get the kube-proxy pods back in a running state.
        ```
       </details>

    3. Check Solution

       <details>

        ```
         The kube-dns service is not working as expected. The first thing to check is if the service has a valid endpoint? Does it point to the kube-dns/core-dns?

         Run: kubectl -n kube-system get ep kube-dns

         If there are no endpoints for the service, inspect the service and make sure it uses the correct selectors and ports.

         Run: kubectl -n kube-system describe svc kube-dns

         Note that the selector used is: k8s-app=core-dns

         If you compare this with the label set on the coredns deployment and its pods, you will see that the selector should be k8s-app=kube-dns

         Modify the kube-dns service and update the selector to k8s-app=kube-dns
         (Easiest way is to use the kubectl edit command)
        ```
       </details>

<br><br><br>

# Practice Test for Advance Kubectl Commands

  - Take me to [Advance Practice Test for Kubectl Commands](https://kodekloud.com/topic/practice-test-advanced-kubectl-commands/)

  ### Solution

   1. Check Solution 

       <details>
       
        ```
        kubectl get nodes -o json > /opt/outputs/nodes.json
        ```   
       </details>

   2. Check Solution 

       <details>

        ```
        kubectl get node node01 -o json > /opt/outputs/node01.json
        ```   
       </details>

   3. Check Solution

       <details>

        ```
        kubectl get nodes -o=jsonpath='{.items[*].metadata.name}' > /opt/outputs/node_names.txt
        ```
       </details>

   4. Check Solution

       <details>

        ```
        kubectl get nodes -o jsonpath='{.items[*].status.nodeInfo.osImage}' > /opt/outputs/nodes_os.txt
        ```
       </details>

   5. Check Solution

       <details>

        ```
        kubectl config view --kubeconfig=my-kube-config -o jsonpath="{.users[*].name}" > /opt/outputs/users.txt
        ```
       </details>

   6. Check Solution

       <details>

        ```
        kubectl get pv --sort-by=.spec.capacity.storage > /opt/outputs/storage-capacity-sorted.txt
        ```
       </details>

   7. Check Solution

       <details>

        ```
        kubectl get pv --sort-by=.spec.capacity.storage -o=custom-columns=NAME:.metadata.name,CAPACITY:.spec.capacity.storage > /opt/outputs/pv-and-capacity-sorted.txt
        ```
       </details>

   8. Check Solution

       <details>

        ```
        kubectl config view --kubeconfig=my-kube-config -o jsonpath="{.contexts[?(@.context.user=='aws-user')].name}" > /opt/outputs/aws-context-name
        ```
       </details>
       
<br><br><br>

# Lightining Lab 1

  - I am ready! [Take me to Lightning Lab 1](https://kodekloud.com/topic/lightning-lab-1-2/)

## Solution to LL-1

   1. Use below commands step-by-step as mentioned:

      <details>
   
      ```
      On Controlplane Node:-

      kubectl drain controlplane --ignore-daemonsets
      apt-get install kubeadm=1.20.0-00
      kubeadm  upgrade plan
      kubeadm  upgrade apply v1.20.0
      apt-get install kubelet=1.20.0-00
      systemctl daemon-reload
      systemctl restart kubelet
      kubectl uncordon controlplane
      kubectl drain node01 --ignore-daemonsets
      
      
      On Worker Node:-
      
      apt-get update
      apt-get install kubeadm=1.20.0-00
      kubeadm upgrade node
      apt-get install kubelet=1.20.0-00
      systemctl daemon-reload
      systemctl restart kubelet     

      Back on Controlplane Node:-
      
      kubectl uncordon node01
      kubectl get pods -o wide | grep gold (make sure this is scheduled on controlplane node)
      ```
      </details>

   2. Execute below command:

      <details>
   
      ```
      kubectl -n admin2406 get deployment -o custom-columns=DEPLOYMENT:.metadata.name,CONTAINER_IMAGE:.spec.template.spec.containers[].image,READY_REPLICAS:.status.readyReplicas,NAMESPACE:.metadata.namespace --sort-by=.metadata.name > /opt/admin2406_data
      ```
      </details>

   3. Use below command and fix the issue:

      <details>

      ```
      Make sure the port for the kube-apiserver is correct.

      Change port from 2379 to 6443 using below command
      
      vi /root/CKA/admin.kubeconfig

      Now replace the port 2379 with 6443
      
      Run:
      
      kubectl cluster-info --kubeconfig /root/CKA/admin.kubeconfig
      ```
      </details>
    
   4. Use below command for the solution:

      <details>
     
      ```
      kubectl create deployment nginx-deploy --image=nginx:1.16
      kubectl set image deployment/nginx-deploy nginx=nginx:1.17 --record
      ```
      </details>
    
   5. Apply/refer below yaml to create a PersistentVolumeClaim:
      
      <details>

      ```
      apiVersion: v1
      kind: PersistentVolumeClaim
      metadata:
        name: mysql-alpha-pvc
        namespace: alpha
      spec:
        accessModes:
        - ReadWriteOnce
        resources:
          requests:
            storage: 1Gi
        storageClassName: slow
      ```
      </details>
  
   6. Execute below command for etcd backup:

      <details>

      ```
      ETCDCTL_API='3' etcdctl snapshot save --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key --endpoints=127.0.0.1:2379 /opt/etcd-backup.db
      ```
      </details>

   7. Apply below manifest for the solution:

      <details>

      ```
      apiVersion: v1
      kind: Pod
      metadata:
        creationTimestamp: null
        labels:
          run: secret-1401
        name: secret-1401
        namespace: admin1401
      spec:
        volumes:
        - name: secret-volume
          secret:
            secretName: dotfile-secret
        containers:
        - command:
          - sleep
          args:
          - "4800"
          image: busybox
          name: secret-admin
          volumeMounts:
          - name: secret-volume
            readOnly: true
            mountPath: "/etc/secret-volume"     
      ```
      </details>

<br><br><br>

# Mock Exam 1

  Test My Knowledge, Take me to [Mock Exam 1](https://kodekloud.com/topic/mock-exam-1-3/)

  #### Solution to the Mock Exam 1

  1. Apply below manifests:

     <details>
     
     ```
     apiVersion: v1
     kind: Pod
     metadata:
       creationTimestamp: null
       labels:
         run: nginx-pod
       name: nginx-pod
     spec:
       containers:
       - image: nginx:alpine
         name: nginx-pod
         resources: {}
       dnsPolicy: ClusterFirst
       restartPolicy: Always
     status: {}
     ```
     </details>

  2. Run below command which create a pod with labels:

     <details>
     
     ```
     kubectl run messaging --image=redis:alpine --labels=tier=msg
     ```
     </details>

 
  3. Run below command to create a namespace:
     
     <details>

     ```
     kubectl create namespace apx-x9984574
     ```
     </details>

  4. Use the below command which will redirect the o/p:

     <details>

     ```
     kubectl get nodes -o json > /opt/outputs/nodes-z3444kd9.json
     ```
     </details>

  5. Execute below command which will expose the pod on port 6379:

     <details>

     ```
     kubectl expose pod messaging --port=6379 --name messaging-service
     ```
     </details>

  6. Apply below manifests:

     <details>

      ```
      apiVersion: apps/v1
      kind: Deployment
      metadata:
        creationTimestamp: null
        labels:
          app: hr-web-app
        name: hr-web-app
      spec:
        replicas: 2
        selector:
          matchLabels:
            app: hr-web-app
        strategy: {}
        template:
          metadata:
            creationTimestamp: null
            labels:
              app: hr-web-app
          spec:
            containers:
            - image: kodekloud/webapp-color
              name: webapp-color
              resources: {}
      status: {}
      ```
      
      In v1.19, we can add `--replicas` flag with `kubectl create deployment` command:
      ```
      kubectl create deployment hr-web-app --image=kodekloud/webapp-color --replicas=2
      ```
     </details>

  7. To Create a static pod, copy it to the static pods directory. In this case, it is `/etc/kubernetes/manifests`. Apply below manifests:

     <details>

     ```
     apiVersion: v1
     kind: Pod
     metadata:
       creationTimestamp: null
       labels:
         run: static-busybox
       name: static-busybox
     spec:
       containers:
       - command:
         - sleep
         - "1000"
         image: busybox
         name: static-busybox
         resources: {}
       dnsPolicy: ClusterFirst
       restartPolicy: Always
     status: {}
     ```
     </details>

  8. Run below command to create a pod in namespace `finance`:

     <details>

     ```
     kubectl run temp-bus --image=redis:alpine -n finance
     ```
     </details>

  9. Run below command and troubleshoot step by step:

     <details>

     ```
     kubectl describe pod orange
     ```

     Export the running pod using below command and correct the spelling of the command **`sleeeep`** to **`sleep`** 

     ```
     kubectl get pod orange -o yaml > orange.yaml
     ```
   
     Delete the running Orange pod and recreate the pod using command.
     
     ```
     kubectl delete pod orange
     kubectl create -f orange.yaml
     ```
     </details>

  10. Apply below manifests:

      <details>

      ```
      apiVersion: v1
      kind: Service
      metadata:
        creationTimestamp: null
        labels:
          app: hr-web-app
        name: hr-web-app-service
      spec:
        ports:
        - port: 8080
          protocol: TCP
          targetPort: 8080
          nodePort: 30082
        selector:
          app: hr-web-app
        type: NodePort
      status:
        loadBalancer: {}
      ```
      </details>

  11. Run the below command to redirect the o/p:

      <details>

      ``` 
      kubectl get nodes -o jsonpath='{.items[*].status.nodeInfo.osImage}' > /opt/outputs/nodes_os_x43kj56.txt
      ```
      </details>

  12. Apply the below manifest to create a PV:

      <details>
     
       ```
       apiVersion: v1
       kind: PersistentVolume
       metadata:
         name: pv-analytics
       spec:
         capacity:
           storage: 100Mi
         volumeMode: Filesystem
         accessModes:
           - ReadWriteMany
         hostPath:
             path: /pv/data-analytics
       ```
       </details>

<br><br><br>

# Mock Exam 2 Solution
  
  
  1. Run the below command for solution:

     <details>

     ```
     ETCDCTL_API=3 etcdctl snapshot save --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key --endpoints=127.0.0.1:2379 /opt/etcd-backup.db
     ```
     </details>

  2. Run the below command for solution:

     <details>
 
     ```
     apiVersion: v1
     kind: Pod
     metadata:
        creationTimestamp: null
        labels:
          run: redis-storage
        name: redis-storage
     spec:
      volumes:
      - name: redis-storage
        emptyDir: {}
      
      containers:
      - image: redis:alpine
        name: redis-storage
        resources: {}
        volumeMounts:
        - name: redis-storage
          mountPath: /data/redis
      dnsPolicy: ClusterFirst
      restartPolicy: Always
     status: {}
     ```
     </details>
 
  3. Run the below command for solution:

     <details>

     ```
     apiVersion: v1
     kind: Pod
     metadata:
       creationTimestamp: null
       name: super-user-pod
     spec:
       containers:
       - image: busybox:1.28
         name: super-user-pod
         command: ["sleep", "4800"]
         securityContext:
           capabilities:
             add: ["SYS_TIME"]
     ```
     </details>

  4. Run the below command for solution:

     <details>
     
     ```
     apiVersion: v1
     kind: PersistentVolumeClaim
     metadata:
       name: my-pvc
     spec:
       accessModes:
         - ReadWriteOnce
       resources:
         requests:
           storage: 10Mi      
     ```
    
     ```
     apiVersion: v1
     kind: Pod
     metadata:
       creationTimestamp: null
       labels:
         run: use-pv
       name: use-pv
     spec:
       containers:
       - image: nginx
         name: use-pv
         volumeMounts:
         - mountPath: "/data"
           name: mypod
       volumes:
       - name: mypod
         persistentVolumeClaim:
           claimName: my-pvc
     ```
     </details>

  5. Run the below command for solution:

     <details>
 
     For Kubernetes Version <=1.17
 
     ```
     kubectl run nginx-deploy --image=nginx:1.16 --replicas=1 --record
     kubectl rollout history deployment nginx-deploy
     kubectl set image deployment/nginx-deploy nginx=nginx:1.17 --record
     kubectl rollout history deployment nginx-deploy
     ```
 
     For Kubernetes Version >1.17
 
     ```
     kubectl create deployment nginx-deploy --image=nginx:1.16 --dry-run=client -o yaml > deploy.yaml
   
     apiVersion: apps/v1
     kind: Deployment
     metadata:
       name: nginx-deploy
     spec:
       replicas: 1
       selector:
         matchLabels:
           app: nginx-deploy
       strategy: {}
       template:
         metadata:
           creationTimestamp: null
           labels:
             app: nginx-deploy
         spec:
           containers:
           - image: nginx:1.16
             name: nginx
     ```
     
     ```
     kubectl create -f deploy.yaml --record
     kubectl rollout history deployment nginx-deploy
     kubectl set image deployment/nginx-deploy nginx=nginx:1.17 --record
     kubectl rollout history deployment nginx-deploy
     ```
     </details>
  
  6. Run the below command for solution:

     <details>
 
     ```
     apiVersion: certificates.k8s.io/v1
     kind: CertificateSigningRequest
     metadata:
       name: john-developer
     spec:
       signerName: kubernetes.io/kube-apiserver-client
       request:  LS0tLS1CRUdJTiBDRVJUSUZJQ0FURSBSRVFVRVNULS0tLS0KTUlJQ1ZEQ0NBVHdDQVFBd0R6RU5NQXNHQTFVRUF3d0VhbTlvYmpDQ0FTSXdEUVlKS29aSWh 2Y05BUUVCQlFBRApnZ0VQQURDQ0FRb0NnZ0VCQU00cS95V0ozQUt1MW9YYmFSQm1QcnpQOHZZME1MN1VjajFIUTlFd1VtUFRYL09pCmtBMGV3UitJcEd3Wk N0dEd5WjNCd3RPUUNlK0ljdXNPdk9LaGFKVVVPamhuOUk1SGFnUElrb2drNW1sU1VWbmkKUjlRZ3NKYTZmeFpYTVdYR0NkZWo1MTdkWkNRVXZ6RXZ3bWZuY W9iMExNRDlHYWtyVXBuZVByTlZLMEdRTU4rTwppQXRzeU16K1lsYWFKblB3QWlWVlZsU1lWclE1TXo5b1J5TjJoU2VVdnAxZGJLSCtVRTBRK2R3UHkvc2hp TGhxCnI5ZjJQb3I3NHQyeHFRei9hYjhwaFltb29kV3d3UDFzRkNON25OL1hRODU5b3BmNjdnVUFRMEdTNFJmZFoxNnMKRnJkOU5FV2NIRUdLTEJzQ2FmZTB 4OURhNnJrcFZaNXVEMnY1SnZjQ0F3RUFBYUFBTUEwR0NTcUdTSWIzRFFFQgpDd1VBQTRJQkFRQWVTRWZ1bW5VK2tFdXR2QlVuNlBwS0d0MnB1TWUyL0pwRU lFb1liOGlkS2tSa2VjVWxHWE0vCnMwc0hjdDFvcnF2SHVBVktLQ0ozK05hcHU4OFp3a3pLakZFUnZ1M1FOZ3BlMEt0R0gzMGcvY09EQ29XTDIwOXQKSGRsW nNpak40OVZ0dXNCaFRjYWFlaU1uZzVsYWJHTCszcmpla1JyZVpWejVSY1BXNlVOczJudFdVVWQzZnl3SApRTlhMNHYzNkcwbzI5NmVaQStOMmNWZzhlS2tx dXlrcVh1TWpBK2xuQVN1QXU2VGVRNU9yMnRSVnRVSXliZUZ3CnlrR2hDUGkzdEliaEsvRkIrYytWY0JNdnlGb0dpcm8vamVxK2E2aFFLK1VKNHB6SDdNM04 3TW9oT2FvU2VjOEQKTmtnSThYREowbGNYWkJLZXZZZVd3UFhZZzh1cTdkQ0YKLS0tLS1FTkQgQ0VSVElGSUNBVEUgUkVRVUVTVC0tLS0tCg==
       usages:
       - digital signature
       - key encipherment
       - client auth
       groups:
       - system:authenticated
       ```
 
      ```
      kubectl create role developer --resource=pods --verb=create,list,get,update,delete --namespace=development
      kubectl create rolebinding developer-role-binding --role=developer --user=john --namespace=development
      kubectl auth can-i update pods --as=john --namespace=development
      ```
  
     </details>
 
  7. Run the below command for solution:

     <details>
 
     ```
     kubectl run nginx-resolver --image=nginx
     kubectl expose pod nginx-resolver --name=nginx-resolver-service --port=80 --target-port=80 --type=ClusterIP
     kubectl run test-nslookup --image=busybox:1.28 --rm -it --restart=Never -- nslookup nginx-resolver-service
     kubectl run test-nslookup --image=busybox:1.28 --rm -it --restart=Never -- nslookup nginx-resolver-service > /root/CKA/nginx.svc
 
     Get the IP of the nginx-resolver pod and replace the dots(.) with hyphon(-) which will be used below.
 
     kubectl get pod nginx-resolver -o wide
     kubectl run test-nslookup --image=busybox:1.28 --rm -it --restart=Never -- nslookup <P-O-D-I-P.default.pod> > /root/CKA/nginx.pod
 
     ```
 
     </details>

  8. Run the below command for solution:

     <details>
 
     ```
     kubectl run nginx-critical --image=nginx --dry-run=client -o yaml > static.yaml
     
     cat static.yaml - Copy the contents of this file.
 
     kubectl get nodes -o wide
     ssh node01 
     OR
     ssh <IP of node01>
 
     Check if static-pod directory is present which is /etc/kubernetes/manifests if not then create it.
     mkdir -p /etc/kubernetes/manifests
 
     Paste the contents of the file(static.yaml) copied in the first step to file nginx-critical.yaml.
 
     Move/copy the nginx-critical.yaml to path /etc/kubernetes/manifests/
 
     cp nginx-critical.yaml /etc/kubernetes/manifests
 
     Go back to master node
 
     kubectl get pods 
     ```
 
     </details>

<br><br><br>

# Mock Exam 3 Solution


1. Run the below command for solution: 

     <details>

     ```
     kubectl create serviceaccount pvviewer
     kubectl create clusterrole pvviewer-role --resource=persistentvolumes --verb=list
     kubectl create clusterrolebinding pvviewer-role-binding --clusterrole=pvviewer-role --serviceaccount=default:pvviewer
     ```

     ```
     apiVersion: v1
     kind: Pod
     metadata:
       creationTimestamp: null
       labels:
         run: pvviewer
       name: pvviewer
     spec:
       containers:
       - image: redis
         name: pvviewer
         resources: {}
       serviceAccountName: pvviewer
     ```
     </details>

2. Run the below command for solution: 

     <details>
 
     ```
     kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="InternalIP")].address}' > /root/CKA/node_ips
     ```
     </details>
 
3. Run the below command for solution:  
 
     <details>
 
     ```
     apiVersion: v1
     kind: Pod
     metadata:
       name: multi-pod
     spec:
       containers:
       - image: nginx
         name: alpha
         env:
         - name: name
           value: alpha
       - image: busybox
         name: beta
         command: ["sleep", "4800"]
         env:
         - name: name
           value: beta
     status: {}
     ```
     </details>
 
4. Run the below command for solution:
 
     <details>
     
     ```
     apiVersion: v1
     kind: Pod
     metadata:
       name: non-root-pod
     spec:
       securityContext:
         runAsUser: 1000
         fsGroup: 2000
       containers:
       - name: non-root-pod
         image: redis:alpine
     ```
     </details>
 
5. Run the below command for solution:  
 
     <details>
 
     ```
     apiVersion: networking.k8s.io/v1
     kind: NetworkPolicy
     metadata:
       name: ingress-to-nptest
       namespace: default
     spec:
       podSelector:
         matchLabels:
           run: np-test-1
       policyTypes:
       - Ingress
       ingress:
       - ports:
         - protocol: TCP
           port: 80
     ```
     </details>
   
6. Run the below command for solution: 
 
     <details>
 
     ```
     kubectl taint node node01 env_type=production:NoSchedule
     ```

     Deploy `dev-redis` pod and to ensure that workloads are not scheduled to this `node01` worker node.
     ```
     kubectl run dev-redis --image=redis:alpine

     kubectl get pods -owide
     ```

     Deploy new pod `prod-redis` with toleration to be scheduled on `node01` worker node.
     ```
     apiVersion: v1
     kind: Pod
     metadata:
       name: prod-redis
     spec:
       containers:
       - name: prod-redis
         image: redis:alpine
       tolerations:
       - effect: NoSchedule
         key: env_type
         operator: Equal
         value: production     
     ```

     View the pods with short details: 
     ```
     kubectl get pods -owide | grep prod-redis
     ```
     </details>
 
7. Run the below command for solution: 
 
     <details>
 
     ```
     kubectl create namespace hr
     kubectl run hr-pod --image=redis:alpine --namespace=hr --labels=environment=production,tier=frontend
     ```
     </details>

8. Run the below command for solution:

     <details>

     ```
     vi /root/CKA/super.kubeconfig

     Change the 2379 port to 6443 and run the below command to verify
     
     kubectl cluster-info --kubeconfig=/root/CKA/super.kubeconfig     
     ```
     </details>

9. Run the below command for solution:
   
     <details>
     
     ```
     sed -i 's/kube-contro1ler-manager/kube-controller-manager/g' kube-controller-manager.yaml
     ```
     </details>

<br><br><br>

# --- END --- 