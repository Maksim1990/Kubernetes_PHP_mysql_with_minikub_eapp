## Kubernetes



## Install kubectl to Ubuntu
https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux

### Install minikube
```
sudo curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && sudo chmod +x minikube && sudo mv minikube /usr/local/bin/
```

### To connect back to minikube Docker deamon
```
eval $(minikube docker-env)
```

### Make sure to run docker without sudo on Ubuntu
```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

### Create webderver deployment & service
```
kubectl create -f webserver.yaml
kubectl create -f webserver-svc.yaml
```

### Create mysql persistent storage, deployment & service
```
kubectl create -f mysql-pv-claim.yaml
kubectl create -f mysql.yaml
kubectl create -f mysql-svc.yaml
```

#### Create table in Kubernetes mysql service

### Rin following command in order to mount local folder
```
minikube start --mount-string ./src:/data --mount
```
### Login for example via MySQLWorkbench and create new table 
```
CREATE TABLE `users` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(100) NOT NULL,
  `last_name` varchar(100) NOT NULL,
  `job_title` varchar(100) DEFAULT NULL,
  `salary` double DEFAULT NULL,
  `notes` text,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

### To connect back to local Docker deamon
```
eval $(minikube docker-env -u)
```

### Kubernetes cheatsheet
### https://kubernetes.io/docs/reference/kubectl/cheatsheet/#deleting-resources
