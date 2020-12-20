# Kubernetes Security Primitives
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808248)
  
In this section, we will take a look at kubernetes security primitives

## Secure Hosts
  
## Secure Kubernetes
- We need to make two types of decisions.
  - Who can access?
  - What can they do?
 

## Authentication
- Who can access the API Server is defined by the Authentication mechanisms.
  
## Authorization
- Once they gain access to the cluster, what they can do is defined by authorization mechanisms.

## TLS Certificates
- All communication with the cluster, between the various components such as the ETCD Cluster, kube-controller-manager, scheduler, api server, as well as those running on the working nodes such as the kubelet and kubeproxy is secured using TLS encryption.

 
## Network Policies
What about communication between applications within the cluster?

  # Authentication
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808250)
  
In this section, we will take a look at authentication in a kubernetes cluster

## Accounts

  
#### Different users that may be accessing the cluster security of end users who access the applications deployed on the cluster is managed by the applications themselves internally.

 
- So, we left with 2 types of users
  - Humans, such as the Administrators and Developers
  - Robots such as other processes/services or applications that require access to the cluster.
  

  
- All user access is managed by apiserver and all of the requests goes through apiserver.
 
 
  
## Authentication Mechanisms
- There are different authentication mechanisms that can be configured.

  
## Authentication Mechanisms - Basic
  
  
## kube-apiserver configuration
- If you set up via kubeadm then update kube-apiserver.yaml manifest file with the option.
  
  
## Authenticate User

- To authenticate using the basic credentials while accessing the API server specify the username and password in a curl command.
  ```
  $ curl -v -k http://master-node-ip:6443/api/v1/pods -u "user1:password123"
  ```

  
- We can have additional column in the user-details.csv file to assign users to specific groups.


# TLS Basics
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808254)
  
In this section, we will take a look at TLS Basics

## Certificate
- A certificate is used to guarantee trust between 2 parties during a transaction.
- Example: when a user tries to access web server, tls certificates ensure that the communication between them is encrypted.

  
  
## Symmetric Encryption
- It is a secure way of encryption, but it uses the same key to encrypt and decrypt the data and the key has to be exchanged between the sender and the receiver, there is a risk of a hacker gaining access to the key and decrypting the data.

  
## Asymmetric Encryption
- Instead of using single key to encrypt and decrypt data, asymmetric encryption uses a pair of keys, a private key and a public key.

  

#### How do you look at a certificate and verify if it is legit?
- who signed and issued the certificate.
- If you generate the certificate then you will have it sign it by yourself; that is known as self-signed certificate.


  
#### How do you generate legitimate certificate? How do you get your certificates singed by someone with authority?
- That's where **`Certificate Authority (CA)`** comes in for you. Some of the popular ones are Symantec, DigiCert, Comodo, GlobalSign etc.


# TLS in kubernetes - Certificate Creation
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808252)
  
In this section, we will take a look at TLS certificate creation in kubernetes

## Generate Certificates
- There are different tools available such as easyrsa, openssl or cfssl etc. or many others for generating certificates.

## Certificate Authority (CA)

- Generate Keys
  ```
  $ openssl genrsa -out ca.key 2048
  ```
- Generate CSR
  ```
  $ openssl req -new -key ca.key -subj "/CN=KUBERNETES-CA" -out ca.csr
  ```
- Sign certificates
  ```
  $ openssl x509 -req -in ca.csr -signkey ca.key -out ca.crt
  ```
 
 
## Generating Client Certificates

#### Admin User Certificates

- Generate Keys
  ```
  $ openssl genrsa -out admin.key 2048
  ```
- Generate CSR
  ```
  $ openssl req -new -key admin.key -subj "/CN=kube-admin" -out admin.csr
  ```
- Sign certificates
  ```
  $ openssl x509 -req -in admin.csr -CA ca.crt -CAkey ca.key -out admin.crt
  ```
  
  
- Certificate with admin privilages
  ```
  $ openssl req -new -key admin.key -subj "/CN=kube-admin/O=system:masters" -out admin.csr
  ```
  

# View Certificate Details
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808260)
  
In this section, we will take a look how to view certificates in a kubernetes cluster.

## View Certs 
 
 - To view the details of the certificate
   ```
   $ openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout
   ```
   

   
#### Follow the same procedure to identify information about of all the other certificates

   
## Inspect Server Logs - Hardware setup
- Inspect server logs using journalctl
  ```
  $ journalctl -u etcd.service -l
  ```
  
  
## Inspect Server Logs - kubeadm setup
- View logs using kubectl
  ```
  $ kubectl logs etcd-master
  ```
  
- View logs using docker ps and docker logs
  ```
  $ docker ps -a
  $ docker logs <container-id>
  ```

# Certificate API
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808253)
  
In this section, we will take a look at how to manage certificates and certificate API's in kubernetes

## CA (Certificate Authority)
- The CA is really just the pair of key and certificate files that we have generated, whoever gains access to these pair of files can sign any certificate for the kubernetes environment.

#### Kubernetes has a built-in certificates API that can do this for you. 
- With the certificate API, we now send a certificate signing request (CSR) directly to kubernetes through an API call.
   

   
#### This certificate can then be extracted and shared with the user.
- A user first creates a key
  ```
  $ openssl genrsa -out jane.key 2048
  ```
- Generates a CSR
  ```
  $ openssl req -new -key jane.key -subj "/CN=jane" -out jane.csr 
  ```
- Sends the request to the administrator and the adminsitrator takes the key and creates a CSR object, with kind as "CertificateSigningRequest" and a encoded "jane.csr"
  ```
  apiVersion: certificates.k8s.io/v1beta1
  kind: CertificateSigningRequest
  metadata:
    name: jane
  spec:
    groups:
    - system:authenticated
    usages:
    - digital signature
    - key encipherment
    - server auth
    request:
      <certificate-goes-here>
  ```
  $ cat jane.csr |base64 
  $ kubectl create -f jane.yaml
  ```
 
  
- To list the csr's
  ```
  $ kubectl get csr
  ```
- Approve the request
  ```
  $ kubectl certificate approve jane
  ```
- To view the certificate
  ```
  $ kubectl get csr jane -o yaml
  ```
- To decode it
  ```
  $ echo "<certificate>" |base64 --decode
  ```
  
  
#### All the certificate releated operations are carried out by the controller manager. 
- If anyone has to sign the certificates they need the CA Servers, route certificate and private key. The controller manager configuration has two options where you can specify this.


# KubeConfig 
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808258)

In this section, we will take a look at kubeconfig in kubernetes


#### Client uses the certificate file and key to query the kubernetes Rest API for a list of pods using curl.
- You can specify the same using kubectl

  
- We can move these information to a configuration file called kubeconfig. And the specify this file as the kubeconfig option in the command.
  ```
  $ kubectl get pods --kubeconfig config
  ```
  
## Kubeconfig File
- The kubeconfig file has 3 sections
  - Clusters
  - Contexts
  - USers
  
  
- To view the current file being used
  ```
  $ kubectl config view
  ```
- You can specify the kubeconfig file with kubectl config view with "--kubeconfig" flag
  ```
  $ kubectl config veiw --kubeconfig=my-custom-config
  ```
  
  
- How do you update your current context? Or change the current context
  ```
  $ kubectl config view --kubeconfig=my-custom-config
  ```
  
- kubectl config help
  ```
  $ kubectl config -h
  ```
  
# API Groups

  
In this section, we will take a look at API Groups in kubernetes

## To return version and list pods via API's 

 
- The kubernetes API is grouped into multiple such groups based on thier purpose. Such as one for **`APIs`**, one for **`healthz`**, **`metrics`** and **`logs`** etc.

  
 
## API and APIs
- These APIs are catagorized into two.
  - The core group - Where all the functionality exists
    

 
  - The Named group - More organized and going forward all the newer features are going to be made available to these named groups.
  
 
    
- To list all the api groups


  
## Note on accessing the kube-apiserver
- You have to authenticate by passing the certificate files.
  
- An alternate is to start a **`kubeproxy`** client


  
 # Authorization
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808261)
  
In this section, we will take a look at authorization in kubernetes

## Why do you need Authorization in your cluster?
- As an admin, you can do all operations
  ```
  $ kubectl get nodes
  $ kubectl get pods
  $ kubectl delete node worker-2
  ```
  
  
## Authorization Mechanisms
- There are different authorization mechanisms supported by kubernetes
  - Node Authorization
  - Attribute-based Authorization (ABAC)
  - Role-Based Authorization (RBAC)
  - Webhook
  

  
## Authorization Modes
- The mode options can be defined on the kube-apiserver

  
- When you specify multiple modes, it will authorize in the order in which it is specified

# RBAC
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808259)

In this section, we will take a look at RBAC

## How do we create a role?
- Each role has 3 sections
  - apiGroups
  - resources
  - verbs
- create the role with kubectl command
  ```
  $ kubectl create -f developer-role.yaml
  ```

## The next step is to link the user to that role.
- For this we create another object called **`RoleBinding`**. This role binding object links a user object to a role.
- create the role binding using kubectl command
  ```
  $ kubectl create -f devuser-developer-binding.yaml
  ```
- Also note that the roles and role bindings fall under the scope of namespace.
  ```
  apiVersion: rbac.authorization.k8s.io/v1
  kind: Role
  metadata:
    name: developer
  rules:
  - apiGroups: [""] # "" indicates the core API group
    resources: ["pods"]
    verbs: ["get", "list", "update", "delete", "create"]
  - apiGroups: [""]
    resources: ["ConfigMap"]
    verbs: ["create"]
  ```
  ```
  apiVersion: rbac.authorization.k8s.io/v1
  kind: RoleBinding
  metadata:
    name: devuser-developer-binding
  subjects:
  - kind: User
    name: dev-user # "name" is case sensitive
    apiGroup: rbac.authorization.k8s.io
  roleRef:
    kind: Role
    name: developer
    apiGroup: rbac.authorization.k8s.io
  ```

  

## View RBAC
  
- To list roles
  ```
  $ kubectl get roles
  ```
- To list rolebindings
  ```
  $ kubectl get rolebindings
  ```
- To describe role 
  ```
  $ kubectl describe role developer
  ```

    
- To describe rolebinding
  ```
  $ kubectl describe rolebinding devuser-developer-binding
  ```
  

  
#### What if you being a user would like to see if you have access to a particular resource in the cluster.
## Check Access

- You can use the kubectl auth command
  ```
  $ kubectl auth can-i create deployments
  $ kubectl auth can-i delete nodes
  ```
  ```
  $ kubectl auth can-i create deployments --as dev-user
  $ kubectl auth can-i create pods --as dev-user
  ```
  ```
  $ kubectl auth can-i create pods --as dev-user --namespace test
  ```
  
  
## Resource Names
- Note on resource names we just saw how you can provide access to users for resources like pods within the namespace.
  ```
  apiVersion: rbac.authorization.k8s.io/v1
  kind: Role
  metadata:
    name: developer
  rules:
  - apiGroups: [""] # "" indicates the core API group
    resources: ["pods"]
    verbs: ["get", "update", "create"]
    resourceNames: ["blue", "orange"]
  ```  

  # Cluster Roles
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808263)
  
In this section, we will take a look at cluster roles

## Roles
- Roles and Rolebindings are namespaced meaning they are created within namespaces.
  
  
## Namespaces
- Can you group or isolate nodes within  a namespace?
  - No, those are cluster wide or cluster scoped resources. They cannot be associated to any particular namespace.
  
  
- So the resources are categorized as either namespaced or cluster scoped.
  
- To see namespaced resources
  ```
  $ kubectl api-resources --namespaced=true
  ```
- To see non-namespaced resources
  ```
  $ $ kubectl api-resources --namespaced=false
  ```
  
  
## Cluster Roles and Cluster Role Bindings
- Cluster Roles are roles except they are for a cluster scoped resources. Kind as **`CLusterRole`** 
  ```
  apiVersion: rbac.authorization.k8s.io/v1
  kind: ClusterRole
  metadata:
    name: cluster-administrator
  rules:
  - apiGroups: [""] # "" indicates the core API group
    resources: ["nodes"]
    verbs: ["get", "list", "delete", "create"]
  ```
  ```
  apiVersion: rbac.authorization.k8s.io/v1
  kind: ClusterRoleBinding
  metadata:
    name: cluster-admin-role-binding
  subjects:
  - kind: User
    name: cluster-admin
    apiGroup: rbac.authorization.k8s.io
  roleRef:
    kind: ClusterRole
    name: cluster-administrator
    apiGroup: rbac.authorization.k8s.io
  ```
  ```
  $ kubectl create -f cluster-admin-role.yaml
  $ kubectl create -f cluster-admin-role-binding.yaml
  ```
  
  
- You can create a cluster role for namespace resources as well. When you do that user will have access to these resources across all namespaces.

  
# Image Security
  - Take me to [Video Tutorial](https://kodekloud.com/courses/539883/lectures/9808251)

In this section we will take a look at image security

# Image
   
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
  spec:
    containers:
    - name: nginx
      image: nginx
  ```
  
  
# Private Registry
- To login to the registry
  ```
  $ docker login private-registry.io
  ```
- Run the application using the image available at the private registry
  ```
  $ docker run private-registry.io/apps/internal-app
  ```
  
  
- To pass the credentials to the docker untaged on the worker node for that we first create a secret object with credentials in it.
  ```
  $ kubectl create secret docker-registry regcred \
    --docker-server=private-registry.io \ 
    --docker-username=registry-user \
    --docker-password=registry-password \
    --docker-email=registry-user@org.com
  ```
- We then specify the secret inside our pod definition file under the imagePullSecret section 
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
  spec:
    containers:
    - name: nginx
      image: private-registry.io/apps/internal-app
    imagePullSecrets:
    - name: regcred
  ```

  
  # Security Context
  - Take me to [Video Tutorial]()
  
In this section, we will take a look at security context

## Container Security
 ```
 $ docker run --user=1001 ubuntu sleep 3600
 $ docker run -cap-add MAC_ADMIN ubuntu
 ```
 
 
## Kubernetes Security
- You may choose to configure the security settings at a container level or at a pod level.


## Security Context
- To add security context on the container and a field called **`securityContext`** under the spec section.
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: web-pod
  spec:
    securityContext:
      runAsUser: 1000
    containers:
    - name: ubuntu
      image: ubuntu
      command: ["sleep", "3600"]
  ```
  
- To set the same context at the container level, then move the whole section under container section.
  
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: web-pod
  spec:
    containers:
    - name: ubuntu
      image: ubuntu
      command: ["sleep", "3600"]
      securityContext:
        runAsUser: 1000
  ```
  
- To add capabilities use the **`capabilities`** option
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: web-pod
  spec:
    containers:
    - name: ubuntu
      image: ubuntu
      command: ["sleep", "3600"]
      securityContext:
        runAsUser: 1000
        capabilities: 
          add: ["MAC_ADMIN"]
  ```
  
 # Network Policies
  - Take me to [Video Tutorials](https://kodekloud.com/courses/539883/lectures/9948740)
  
#### Trafic flowing through a webserver serving frontend to users an app server serving backend API and a database server

  
- There are two types of traffic
  - Ingress
  - Egress
  
## Create network policy
 
- To create a network policy
  ```
  apiVersion: networking.k8s.io/v1
  kind: NetworkPolicy
  metadata:
   name: db-policy
  spec:
    podSelector:
      matchLabels:
        role: db
    policyTypes:
    - Ingress
    ingress:
    - from:
      - podSelector:
          matchLabels:
            role: api-pod
      ports:
      - protocol: TCP
        port: 3306
  ```
  $ kubectl create -f policy-definition.yaml
  ```
  
  
 
 
  
  
  
   
  

   
   

   
  
  

  

  


  
  
  
  
 


  

  
  

  
   

  
  
  

  
  
  
  
  
  

  
  

 
  
  
  