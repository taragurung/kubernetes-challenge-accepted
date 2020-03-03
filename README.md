# Kubernetes challenge accepted

The simple nodejs based application that displays `hello Tara!` and is deployed in minikube. 

## Application setup architecture

[![enter image description here][1]][1]

  [1]: https://i.stack.imgur.com/DTOjJ.png



## Prerequisite

- install minikube (allow us to  setup a kubernetes cluster locally)
- install kubectl ( a kubernetes client for talking to kubernetes cluster)

## Instructions
- Create a docker image using the Dockerfile and necessary files included in the repo.
- Start minikube
- run ``` eval $(minikube docker-env) ``` this will allow us to use local image inside minikube.
- Create a kubernetes deployment using the deploy.yaml manifest inside manifests directory. ``` kubectl apply -f deploy.yaml ```
- Create a kubernetes service using the service.yaml manifest file inside manifests directory. ``` kubectl apply -f service.yaml ```
- enable ingress controller in minikuber using ``` minikube addons enable ingress ``` before running ingress.yaml manifests
- Create a kubernetes ingress controller using the ingress.yaml manifest file inside manifests directory. ``` kubectl apply -f ingress.yaml ```
- Create a configmap resource using the configmap.yaml file. `kubectl apply -f configmap.yaml`


## Adding the configmap to deployments:
We are ready with the setup but here I would like to showcase how we can add the configmap created to the deployment.  The easy way to setup env is with key and value on it but instead of doing so we do the following when using the configmap.

[![enter image description here][2]][2]

  [2]: https://i.stack.imgur.com/YAs4l.png


#### Test Application

```
$ curl $(minikube ip)
Hello Tara!
```

