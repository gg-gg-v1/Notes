1. docker run -> docker run hello-world, image will get pulled from docker hub repo and will run and producde some output for you -> output -> Hello from Docker!
2. docker run -it ubuntu bash -> will download and run the image and redirect yout to conrtainer terminal
3. cat /etc/*release* -> it will show ubuntu host details because by running command in point no 2 we were in ubuntu container
4. docker ps -> list all running Containers but not exited containers.
5. docker ps -a -> list all including exited containers as well
6. docker stop random_name -> random_name is the name of the container that we are stopping, you can stop the container using containerId as well
7. docker images -> to see list of docker images
8. docker rmi ubuntu-> it will remove the image, but before deleting image make sure you delete all dependent containers
9. docker pull ubuntu -> it will just download the image but will not run it so that later on when we run it, it will not pull this image again, its gonna directly run the image.
10.docker exec cool_cannon cat /etc/hosts -> will show the contents of /hosts file in docker container.

11. docker run -d centos sleep 20 -> will runthe containerfor 20seconds and itwillget exited if it doesnt have any service tobe run inside the container, so after  20 seconds docker ps will show nothing.

12.docker rm 345 a0e 774 or docker rm 34 a0 77 -> will remov the cotnainers whose starting 3 letters are 345 a0e and 774.

13. docker exec <container-id> cat /etc/*release* -> its gonna execute the cat command onthe running container and it willshow which versioof os is runing on that particular container.
  
14. docker run ubuntu:17.04 -> willpull 17.04 version with tag '17.04' otherwise latest verion with tag 'latest'.

15. docker run -i simgple-prompt-docker -> will run and gives you option to input your data just like STDIN .

16 attach mode -> docker run someimage, detach mode docker run -d someimage.

17. docker run -d centos sleep 20 -> will runthe containerfor 20seconds and itwillget exited if it doesnt have any service tobe run inside the container, so after  20 seconds docker ps will show nothing.

port mapping:
  
18 docker run -p 80:3000 simple-webapp -> if you access like this http://192.168.1.1:80 [http://<docker-host-ip>] -> it will map public traffic to 3000 port inside the container - here 3000 port is docker container port with someip <172.23.2.2>.

volume mapping:

19. docker run -v /opt/localdatadir:/var/lib/containerdir mysql

20. docker attach <container-id> -> will bring docker container back to foreground.
  
21. docker run -p 8080:8080 jenkins -> will run the jenkinson port 8080 so that you can run this by : hostip:8080

Dockerfile:

```
FROM Ubuntu
RUN apt-get update
RUN apt-get install python
RUN pip install flask
RUN pip install flask-mysql
COPY . /opt/source-code
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

22. docker build . or docker build Dockerfile . -t mydockertag

23. docker run -p 8080:8080 -v /root/my-jenkins-data:/var/jenkins_home jenkins  -> with volume mount if it gives access issue then use below command with "-u root "

24. docker run -p 8080:8080 -v /root/my-jenkins-data:/var/jenkins_home -u root jenkins 

COMMAND and ENTRYPOINT:

25. docker run ubuntu sleep 5 -> docker run ubuntu [COMMAND] -> it will override the default command and conatainer will exit after 5 seconds

26. CMD command param -> CMD sleep 5
    CMD ["command1","param1"] -> CMD ["sleep","5"]

27. 
```
FROM Ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]

try to put entrypoint and cmd in json format
```
above dockerfile will make container to sleep for 5 seconds if we do 'docker run ubuntu-sleeper'
now if I want to run it for 10 seconds then I can run below command 
'docker run ubuntu-sleeper 10' -> its going to override the default 5 seconds with 10 seconds.

now to run the sleep command to sleep2.0 [some other command] use entrypoint runtime to do this.
like this example : docker run --entrypoint sleep2.0 ubuntu-sleeper 20
so effective dockerfile at runtime willbe 
```
FROM Ubuntu
ENTRYPOINT ["sleep2.0"]
CMD ["20"]
```

DOCKER SWARM:

28. its the wayto create replicas of app incase if app on dockerhost is down or dockerhost is down then another dockerhost will be up and running with another created replica of app.
docker manager/master will be one of the docker host and remaining will be worker or slave
docker swarm init --advertise-addr  192.168.1.2 -> will initialize the manager
docker swarm join --token SWMTKN-1-5jmihs2kbv09biyuhd64lvj6jpbggjz8km95g55cxcs06w5107-4hw5a087qd43oe0d61vt9qqw1 192.168.1.2:2377
```
docker-compose.yml

services:
   web:
     image: "somewebapp"
     replicas: 5
  database:
     image: "mysql"     

```
docker stack deploy -c docker-compose.yml -> will create 5 replicas of app in 5 docker host.

Networking :

29. when we isntlal dockr it creates 3 networks- 1.bridge 2.none 3. host
if we run this docker run ubuntu -> it willbein bridge network
if we run this docker run ubuntu --network=none -> it willbein none means no network
if we run this docker run ubuntu --network=host -> it will be in host network

30. 
```
docker network create \
  --driver bridge \
  --subnet 189.1.1.1/12 \
  custom-isolated-network
```
above command will create the new user definer or our custom network


Kubernetes aka k8s

once you setup 3 vms-> 1st as master and other 2 as worker node.

31. sudo apt-get update
32. sudo apt-get install -y docker.io
33. I m skippingthe part shown in video no. 7. Demo - Kubeadm - Part 2 - Configure Cluster with kubeadm -> refer this for aws k8s cluster setup with kubeadm

34. kubeadm init -> to initialize the master

35. kubectl get pods -all-namespaces -> will show all running pods

36. kubectl get pods 

37. kubectl run nginx --image=nginx

38. kubectl delete deployment/nginx

39. kubectl get services -> to get list of services on cluster

40. pod-definition.yml
```
version: v1
api: Pod
metadata:
    name: myapp-pod
    labels:
    	app: myapp
    	type: front-end

spec:
	containers:
		- name: nginx-container
		  image: nginx
```

run below command to create the pod with k8s.
kubectl create -f pod-definition.yml
