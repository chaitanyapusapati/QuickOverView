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