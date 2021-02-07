# WordPress In Kubernetes

## Minikube

Minikube is a tool to run Kubernetes locally. It runs single-node cluster.

### Install by Bash on Mac

```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube
```

### Start Cluster

```shell
minikube start
```

![Screenshot](Screenshot1.png)

## Kubectl

Kubectl is used to deploy and manage clusters resources.

### Install Kubectl

```shell
minikube kubectl -- get po -A
```

![Screenshot](Screenshot2.png)

### Create yaml files

- kustomization.yaml, includes resources file which contains pod deployment  information.

- wordpress-deployment.yaml, in which I used wordpress:5.6-apache from DockerHub.
- mysql-deployment.yaml, provide db for wordpress

### Create deployment

```shell
kubectl apply -k ./
```

![Screenshot](Screenshot3.png)

![Screenshot](Screenshot4.png)

Once deployment is created, corresponding wordpress pod will be deployed into the cluster. We now can see the pods are running.

```
kubectl get pods
```

![Screenshot](Screenshot5.png)

```
kubectl get services wordpress
```

```
minikube service wordpress --url
```

![Screenshot](Screenshot6.png)

Browse http://192.168.64.2:31481/wp-admin/

![Screenshot](Screenshot7.png)

Browse http://192.168.64.2:31481/

![Screenshot](Screenshot8.png)

