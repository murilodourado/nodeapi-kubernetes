# API Example and Kubernetes
Main focus is how to create a deploy in kubernetes, and create configuration to scale out the application. 

This example is required :

* [nodejs](https://nodejs.org/en/)
* [docker](https://docs.docker.com/get-docker/) 
* [minikube](https://kubernetes.io/docs/tasks/tools/)

## Build docker image

To make this images visable to minikube, and use your images locally, the pollicy should be set as *imagePullPolicy: Never* , and execute the command: 
```
$ eval $(minikube docker-env)  

$ docker build -t <your username>/api-node .
```

## Running docker image
```
$ docker run -p 3000:3000 --name api-node -d <your username>/api-node
```
## Kubernetes 

*Running Kubernets* 
```
 $ minikube start 
 $ minikube dashboard (to open k8s dashboard)
 ```

Following commands is an example how to create a POD, Deployments to scale you application, and service to expose and use it.

Create a new pod:
```
$ kubectl create -f ./deploy/pod.yml
```
Create a new deployment:
```
$ kubectl create -f ./deploy/deployment.yml
```
Create a new service to expose the application:
```
$ kubectl create -f ./deploy/service.yml
```
## Calling the api
* curl -X GET localhost:3000
