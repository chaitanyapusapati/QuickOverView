## **Rolling Updates and RollBacks :**

When you first create a deployment it triggers a rollout, A new rollout creates a new deployment revision, let's call it revision 1. In the future when the application is upgraded meaning when the container version is updated to a new one, a new rollout is triggered and a new deployment revision is created named revision 2. This helps us keep track of the changes made to our deployment and enables us to roll back to a previous version of deployment if necessary.

**There are 2 types of deployment strategies :**

Say for example you have five replicas of your web application instance deployed. One way to upgrade these to a newer version is to destroy all of the exixting and then create newer versions of application instances, meaning first destroy the five running instances and then deploy five new instances of the new application version. The problem with this as you can imagine is that during the period after the older versions are down and before any newer version is up, the application is down and inaccessible to users this strategy is known as the **Recreate strategy.** And thankfully this is not the default deployment strategy.

The second strategy is where we did not destroy all of them at once. Instead we take down the older version and bring up a newer version one by one.nThis way the application never goes down and the upgrade is seamless. Remember if you do not specify a strategy while creating the deployment it will assume it to be **Rolling update.** In other words *Rolling update is the default deployment strategy.*

### **Commands :**
**To Create a deployment :**
```
 kubectl create -f deployment-def.yml
```
**To view deployment :**
```
 kubectl get deployments
```
**To update or change :**
``` 
kubectl apply -f <fileName>
kubectl set image deployment/<deploymentName> <container name>=<new-image>
```
**To view status :**
``` kubectl rollout status deployment/<deploymentName>
kubectl rollout history deployment/<deploymentName>
```
**To Rollback changes :**
```
 kubectl rollout undo deployment/<deploymentName>
 ```

 # Commands and Arguments in Docker
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808205)
  
In this section, we will take a look at commands and arguments in docker

- To run a docker container
  ```
  $ docker run ubuntu
  ```
- To list running containers
  ```
  $ docker ps 
  ```
- To list all containers including that are stopped
  ```
  $ docker ps -a
  ```
  
  
#### Unlike virtual machines, containers are not meant to host operating system.
- Containers are meant to run a specific task or process such as to host an instance of a webserver or application server or a database server etc.

  
  
#### How do you specify a different command to start the container?
- One Option is to append a command to the docker run command and that way it overrides the default command specified within the image.
  ```
  $ docker run ubuntu sleep 5
  ```
- This way when the container starts it runs the sleep program, waits for 5 seconds and then exists. How do you make that change permenent?
  
 
  
- There are different ways of specifying the command either the command simply as is in a shell form or in a JSON array format.
 
 
- Now, build the docker image
  ```
  $ docker build -t ubuntu-sleeper .
  ```
- Run docker container
  ```
  $ docker run ubuntu-sleeper
  ```
  
  
## Entrypoint Instruction
- The entrypoint instruction is like the command instruction as in you can specify the program that will be run when the container starts and whatever you specify on the command line.


# Commands and Arguments in Kubernetes
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808202)

In this section, we will take a look at commands and arguments in kubernetes

- Anything that is appended to the docker run command will go into the **`args`** property of the pod definition file in the form of an array.
- The command field corresponds to the entrypoint instruction in the Dockerfile so to summarize there are 2 fields that correspond to 2 instructions in the Dockerfile.
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: ubuntu-sleeper-pod
  spec:
   containers:
   - name: ubuntu-sleeper
     image: ubuntu-sleeper
     command: ["sleep2.0"]
     args: ["10"]
  ```

  # Configure Environment Variables In Applications
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/10589125)
  
#### ENV variables in Docker
```
$ docker run -e APP_COLOR=pink simple-webapp-color
```

#### ENV variables in kubernetes 
- To set an environment variable set an **`env`** property in pod definition file.
  
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: simple-webapp-color
  spec:
   containers:
   - name: simple-webapp-color
     image: simple-webapp-color
     ports:
     - containerPort: 8080
     env:
     - name: APP_COLOR
       value: pink
  ```
  
- There are other ways of setting the environment variables such as **`ConfigMaps`** and **`Secrets`**


# Configure ConfigMaps in Applications
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/10589128)
  
In this section, we will take a look at configuring configmaps in applications

## ConfigMaps
- There are 2 phases involved in configuring ConfigMaps. 
  - First, create the configMaps
  - Second, Inject then into the pod.
- There are 2 ways of creating a configmap.
  - The Imperative way
    ```
    $ kubectl create configmap app-config --from-literal=APP_COLOR=blue --from-literal=APP_MODE=prod
    $ kubectl create configmap app-config --from-file=app_config.properties (Another way)
    ```
    
  - The Declarative way
    
    ```
    apiVersion: v1
    kind: ConfigMap
    metadata:
     name: app-config
    data:
     APP_COLOR: blue
     APP_MODE: prod
    ```
    ```
    Create a config map definition file and run the 'kubectl create` command to deploy it.
    $ kubectl create -f config-map.yaml
    ```
  
    
 ## View ConfigMaps
 - To view configMaps
   ```
   $ kubectl get configmaps (or)
   $ kubectl get cm
   ```
 - To describe configmaps
   ```
   $ kubectl describe configmaps
   ```
   

   
 ## ConfigMap in Pods
 - Inject configmap in pod
   ```
   apiVersion: v1
   kind: Pod
   metadata:
     name: simple-webapp-color
   spec:
    containers:
    - name: simple-webapp-color
      image: simple-webapp-color
      ports:
      - containerPort: 8080
      envFrom:
      - configMapRef:
          name: app-config
   ```
   ```
   apiVersion: v1
   kind: ConfigMap
   metadata:
     name: app-config
   data:
     APP_COLOR: blue
     APP_MODE: prod
   ```
   ```
   $ kubectl create -f pod-definition.yaml
   ```
  
   
 #### There are other ways to inject configuration variables into pod   
 - You can inject it as a **`Single Environment Variable`** 
 - You can inject it as a file in a **`Volume`**
 
   
# Secrets
  - Take me to [Video Tutorials](https://kodekloud.com/courses/539883/lectures/9808207)

In this section, we will take a look at secrets in kubernetes

## Web-Mysql Application

 
- One way is to move the app properties/envs into a configmap. But the configmap stores data into a plain text format. It is definitely not a right place to store a password.
  ```
  apiVersion: v1
  kind: ConfigMap
  metadata:
   name: app-config
  data:
    DB_Host: mysql
    DB_User: root
    DB_Password: paswrd
  ```
  
- Secrets are used to store sensitive information. They are similar to configmaps but they are stored in an encrypted format or a hashed format.

#### There are 2 steps involved with secrets
- First, Create a secret
- Second, Inject the secret into a pod.
  
  
#### There are 2 ways of creating a secret
- The Imperative way
  ```
  $ kubectl create secret generic app-secret --from-literal=DB_Host=mysql --from-literal=DB_User=root --from-literal=DB_Password=paswrd
  $ kubectl create secret generic app-secret --from-file=app_secret.properties
  ```
  
- The Declarative way
  ```
  Generate a hash value of the password and pass it to secret-data.yaml definition value as a value to DB_Password varaible.
  $ echo -n "mysql" |base64
  $ echo -n "root" |base64
  $ echo -n "paswrd"|base64
  ```
  
  Create a secret definition file and run `kubectl create` to deploy it
  ```
  apiVersion: v1
  kind: Secret
  metadata:
   name: app-secret
  data:
    DB_Host: bX1zcWw=
    DB_User: cm9vdA==
    DB_Password: cGFzd3Jk
  ```
  ```
  $ kubectl create -f secret-data.yaml
  ```

  
## Encode Secrets

  
## View Secrets
- To view secrets
  ```
  $ kubectl get secrets
  ```
- To describe secret
  ```
  $ kubectl describe secret
  ```
- To view the values of the secret
  ```
  $ kubectl get secret app-secret -o yaml
  ```
  
  
## Decode Secrets
- To decode secrets
  ```
  $ echo -n "bX1zcWw=" |base64 --decode
  $ echo -n "cm9vdA==" |base64 --decode
  $ echo -n "cGFzd3Jk" |base64 --decode
  ```
  
## Configuring secret with a pod
- To inject a secret to a pod add a new property **`envFrom`** followed by **`secretRef`** name and then create the pod-definition
  
  ```
  apiVersion: v1
  kind: Secret
  metadata:
   name: app-secret
  data:
    DB_Host: bX1zcWw=
    DB_User: cm9vdA==
    DB_Password: cGFzd3Jk
  ```
  ```
   apiVersion: v1
   kind: Pod
   metadata:
     name: simple-webapp-color
   spec:
    containers:
    - name: simple-webapp-color
      image: simple-webapp-color
      ports:
      - containerPort: 8080
      envFrom:
      - secretRef:
          name: app-secret
   ```
  ```
  $ kubectl create -f pod-definition.yaml
  ```
  
#### There are other ways to inject secrets into pods.
- You can inject as **`Single ENV variable`**
- You can inject as whole secret as files in a **`Volume`**

  
## Secrets in pods as volume
- Each attribute in the secret is created as a file with the value of the secret as its content.
  

  # Multi-Container Pods
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/10589155)

In this section, we will take a look at multi-container pods

## Monolith and Microservices

  
#### Multi-Container Pods

  
- To create a new multi-container pod, add the new container information to the pod definition file.
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: simple-webapp
    labels:
      name: simple-webapp
  spec:
    containers:
    - name: simple-webapp
      image: simple-webapp
      ports:
      - ContainerPort: 8080
    - name: log-agent
      image: log-agent
  ```

