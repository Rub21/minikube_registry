## Run docker local images in minikube
 
This a simple test local images in minikube, uses will be in [osm-seed](https://github.com/developmentseed/osm-seed)
 
# Start minikube
 
```sh
minikube stop
minikube delete --all
minikube start --mount-string=$PWD/data/:/mnt/ --mount --driver=docker
```
 
There are a several ways to add images into minikube https://minikube.sigs.k8s.io/docs/handbook/pushing/
 
#### Build container inside of minikube environment and run on it
 
```
eval $(minikube docker-env)
docker ps
docker-compose build
kubectl create deployment nginx --image=webserver:v1
kubectl expose deployment nginx --type=NodePort --port=80
kubectl get service nginx
minikube service nginx --url
```
 
*Note: Also docker local images can be loaded into minikube, but  for huge images takes time*
 
```
minikube image load webserver:v1



