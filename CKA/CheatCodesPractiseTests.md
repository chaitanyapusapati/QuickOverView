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

