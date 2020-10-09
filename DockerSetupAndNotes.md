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

port mapping:
  
17 docker run -p 80:3000 simple-webapp -> if you access like this http://192.168.1.1:80 [http://<docker-host-ip>] -> it will map public traffic to 3000 port inside the container - here 3000 port is docker container port with someip <172.23.2.2>.
  
  
