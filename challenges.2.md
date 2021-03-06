# Kubernetes 101 Challenge
> For scheduling applications consisting of multiple containers you typically use an orchestrator. Kubernetes is an orchestrator and in this chapter you will set up a Kubernetes cluster in Azure Kubernetes Service (AKS) and an Azure Container Registry (ACR) to store your images.

![](/img/challenge2.png)

## Here's what you'll learn:
> - How to set up a Kubernetes Cluster with Azure Kubernetes Services
> - How to access the cluster with the commandline command "kubectl"
> - Get to know the basic command set of "kubectl"
> - Understand the concept of pods and services and how they come together
> - Get in touch with Yaml files to specify a desired state for a Kubernetes object


## 1. Create a Kubernetes cluster on Azure Container Services 
- Set up your Kuberenetes cluster using Azure Kubernetes Services.
> Need help? Check hints [here :blue_book:](hints/create_aks_cluster.md)!

The deployment will take some time (~20 min). 

## 2. Run single container app in your K8s cluster
> This is about running your first container in Kubernetes
> Need help? Check hints [here :blue_book:](hints/k8sSingle.md)!

- Run a public available application in a single container on your cluster. The image name is "nginx".
    - Use the "kubectl run" command
- Add a service to make your application accessible from the internet
    - Use the "kubectl expose" command and "kubectl edit YOURSERVICE" command.
- Start your webbrowser to view your application running in your cluster.

## 3. Kubernetes discovery
> This is about learning the Kubernetes objects
> Need help? Check hints [here :blue_book:](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)!

- If you want to work with namespaces. Create your own namespace 'dennisspace' with 
```
kubectl create ns dennisspace
```
and apply this postfix to your  kubectl commands like 
```
kubectl get pods -n dennisspace
```

- Familiarize yourself with the following commands on commandline, eg.
```
kubectl get pods    // to display all pods
kubectl get svc     // to display all services
kubectl get deployments     // to display all deployments
kubectl delete pods/<podid> // to delete a specific pod
kubectl describe deployment <deploymentname> // look up yaml for a deployment
```

## 4. Execute deployments via yaml
> This is about creating a desired state configration for your apps
> Need help? Check hints [here :blue_book:](hints/learn_yaml_files.md)! [here :blue_book:](hints/create_secrets.md)!
- Launch the nginx deployment via yaml file (see if you can download it somewhere?)
- Launch a custom image from your registry (learn about secrets or registry authentication)  [here :blue_book:](hints/yaml/aci-helloworld.yaml)!
- You can declare a namespace inside your yaml file
- Delete the frontend pod using the commandline and call the website again. 
- You'll recognize that it will no longer work - but they restart?

## BONUS Challenge - Scaling apps automatically
> Need help? Check hints [here :blue_book:](hints/create_traffic.md)!

- Configure your deployment to ensure that the number of replicas scales automatically according to the load
- Configure a horizontal pod autoscaler for your deployment
- Create some traffic to ensure that the scale operation starts
- Evaluate the azure monitor to see performance metrics