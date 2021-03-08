# Kubernetes Study Notes

- [Terminologies](#Terminologies)
- [Steps](#Steps)
    * [Setting up a Kubernete Cluster](#Setting up a Kubernete Cluster)
    * [Deploying Docker to a Kubernete Cluster](#Deploying Docker to a Kubernete Cluster)
        + [Notes](#Notes)

## Terminologies
- Kubernetes (K8s)
    - a containers orchestration system
- Cluster
    - A set of worker machines, called nodes, that run containerized applications
    - Every cluster has at least one worker node
- Docker
    - allows users to put application inside a container
- Container
    - "A lightweight and portable executable image that contains software and all of its dependencies"
    - store application, dependencies, and its environment that can be run on different machines 
    - avoid environment conflicts / problems caused by same application running on different environments
    - think how different browsers support web apps / function differently?
- Docker Compose
    - allow user to host different containers
    - all the containers together acts as a container
        - a container for Database, one for webservice, for example
    - one way to implement Microservices in software development
-Microservices
    - an architectural design for building a distributed application using containers
    - arranges an application as a collection of loosely coupled services
    - each function of the application stored in the container operates as an independent service
    - allows each independent service to scale / update without interrupting other parts / services within the application / container
    - avoid bottlenecks of a central database
    - improve business capabilities
    - enable continuous delivery and deploying applications

## Steps
1. Setup a Kubernete Cluster
    - this is where you configure the cluster initially
    - decide how many nodes, power, storage etc to use in your cluster
1. Create an application to put inside a Kubernete Cluster, using Docker
1. kubectl - Kubernetes CLI
    - allows user to work with Kubernetes on local machines
    - configure the cluster through a `.yaml` file
1. `.yaml` file
    - allow user to connect to their Kubernetes cluster to work on their local machines


### Setting up a Kubernete Cluster
1. Go to provider of your choice
1. Create a Kuberbete Cluster
    - during this step, you will be choosing the specs (configuring) for the cluster
    - common configuration options include:
        - cluster's name
        - region
        - Kubernetes Version
        - Add node pools 
            - CPU
            - Memories
            - Storage
1. Receive Kubernetes API Endpoints after setup is done
1. Receive and download Kubeconfig to your local machine
    - a '.yaml' file
    - a file that you use to connect to your Cluster
1. install kubectl - Kubernetes CLI on your local machine
    - https://kubernetes.io/docs/tasks/tools/
    - for mac user with homebrew, simply type `$ brew install kubectl` in your terminal
1. If you enter `$ kubectl get nodes` command
    - it will response `error: the server doesn't have a resource type "nodes"
    - it is because kubectl is not connected to the servers/cluster you've just created
1. To connect kubectl to the newly created cluster / server
    - do it through the downloaded '.yaml' file
    - by default, Kubernetes looks for the '.yaml' file at a specific place automatically
        - For Mac, `$ user/.kube/config` is the place!
1. Move '.yaml' file to `$ user/.kube/config` or `$ ~/.kube/config` where Kubernetes would run the file automatically
1. Enter `$ kubectl get nodes` 
    - your local machine is now connected to the Cluster!
    - in the terminal, you will see the returning info of the nodes / clusters you have created in the above steps
1. Enter `$ kubectl get pods -A` 
    - to see all the pods across all the name spaces inside the Kubernetes
    - " A Pod is a Kubernetes abstraction that represents a group of one or more application containers (such as Docker), and some shared resources for those containers."

### Deploying Docker to a Kubernete Cluster
1. `$ kubectl config get-contexts` return a list of cluster you are connected to
    - context = your connection to your cluster(s)
    - come from the end of the '.yaml' file 
        - `$ less ~/.kube/config` to see what's inside the '.yaml' file 
        - you can have multiple '.yaml' files or multiple contexts within a '.yaml' file 

#### Notes
- you can have multiple '.yaml' files or multiple contexts within a '.yaml' file 