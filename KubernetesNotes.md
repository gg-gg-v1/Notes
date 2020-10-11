k8s is orchestration tool, which orchestrate containers for handling them like scaling them or making then up and running etc.
k8s is being installed in node along side minikube.
kubectl is an agent which helps in communication with master node.

SETUP ON LOCAL:

1. install minikube {will install 4 or 5 comps together like api server, etcd, schedular, controller on Master node.}
    brew install minikube

2. install kubectl {this is an agent to be installed on node}
   brew install kubectl 

SAMPLE deployment on local:

Note : with minikube , only you can setup single node cluster . for settinng multinode cluster please use kubeadm
1. run 'minikube start' 

2. kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10
    o/p-> deployment.apps/hello-minikube created
3. kubectl expose  deployment hello-minikube --type=NodePort --port=8080
    o/p-> service/hello-minikube exposed
4. kubectl get pod
```
username-MBP:~ username$ kubectl get pod
NAME                              READY   STATUS              RESTARTS   AGE
hello-minikube-5d9b964bfb-8h4xp   0/1     ContainerCreating   0          2m
username-MBP:~ username$ kubectl get pod
NAME                              READY   STATUS    RESTARTS   AGE
hello-minikube-5d9b964bfb-8h4xp   1/1     Running   0          2m14s
```
5. minikube service hello-minikube --url
```
🏃  Starting tunnel for service hello-minikube.
|-----------|----------------|-------------|------------------------|
| NAMESPACE |      NAME      | TARGET PORT |          URL           |
|-----------|----------------|-------------|------------------------|
| default   | hello-minikube |             | http://127.0.0.1:60123 |
|-----------|----------------|-------------|------------------------|
```
6. 
```
username-MBP:~ username$ kubectl delete deployment
username-MBP:~ username$ kubectl delete services hello-minikube
service "hello-minikube" deleted
username-MBP:~ username$ kubectl delete deployment hello-minikube
deployment.apps "hello-minikube" deleted
username-MBP:~ username$ 
```
