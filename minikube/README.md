Caso prefira o minikube é possivel utilizar o podman junto com o minikube.
```
minikube config set driver podman

minikube start --driver=hyperkit

or

brew install qemu
minikube start --driver=qemu
```

kubectl get all

# Acessar um serviço utilizando minikube URL
```
kubectl create deployment --image=nginx nginx --replicas=4
kubectl expose deployment nginx --type=LoadBalancer --port=80
kubectl get svc
minikube service nginx --url
curl http://192.168.205.4:31385
```


<<<<<<< Updated upstream

controlplane ~ ➜  kubectl replace --force -f ubuntu-sleeper-3.yaml 
pod "ubuntu-sleeper-3" deleted
pod/ubuntu-sleeper-3 replaced
=======
kubectl replace --force -f file.yml
>>>>>>> Stashed changes
