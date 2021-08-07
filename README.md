# minikube-starter
Some basic minikube starter project

## installation


```console
david@bolarque:~$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
david@bolarque:~$ sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
To actually start minikube you'll need a driver, I will use here the Linux Kernel-based VM Driver.

Then set the kvm2 as the default driver for minikube and start it:

```console
david@bolarque:~$ minikube config set driver kvm2
david@bolarque:~$ minikube start
```
You'll have now the kube configuration folder in `~/.kube/config` and you can check if `kubectl` can access your cluster : 

```
kubectl cluster-info
kubectl get po -A

```

Besides Minikube has a dashboard you can access with `minikube dashboard` command.

Enabling bash completion is a must for `kubectl`, how to do this is explained  if you run `kubectl completion -h`.

## create resources

```console
david@bolarque:~/projects/minikube-starter$ k run nginx --image=nginx --port=80 --expose --dry-run=client -o yaml > resources/1-deployment.yaml
david@bolarque:~/projects/minikube-starter$ k create -f resources/
service/nginx created
pod/nginx created
```

## kubctl explain command

Use it as a commnand line alternative to i*net search engines while finding out fileds syntax:
```console
david@bolarque:~/projects/minikube-starter$ k explain pod.spec.containers --recursive
```


## references

[minikube docs](https://minikube.sigs.k8s.io/docs/start/) 

[KVM installation Ubuntu](https://help.ubuntu.com/community/KVM/Installation)

