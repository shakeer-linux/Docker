
**Dockerfile** : a dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. here's a simple dockerfile that copies the "dist" folder to /usr/share/nginx/html:
```
from nginx
copy dist /usr/share/nginx/html
expose 80
```

**project structure**
the dockerfile should be located in the root of the project. here is an example from my project:

how to run the docker container on your local machine
**build
```
docker build -t angular-webpack .
```
**run
```
docker run -p 9000:80 -t angular-webpack
```

Note: this will create a container with the image "angular-webpack" and bind the container’s port 80 to the host machine’s port 9000. after the "docker run -p 9000:80 -it angular-webpack" command, the docker container runs on a linux virtual machine. so we can't run docker natively on windows or a mac. the following properties must be set:
```
set environment properties
set userprofile = c:\users\xxx  --> set your user proile 
set docker_cert_path=%userprofile%\.docker\machine\machines\default
set docker_host=tcp://192.168.99.100 --> find this ip in docker quick start terminal
set docker_machine_name=default
set docker_tls_verify=1
```


**test: http://192.168.99.100:9000/index.html



++++++++++++++++++++++


build docker image
```
docker build -t image-name .
```

run docker image
```
docker run -p 80:80 -it image-name
```
stop all docker containers 
```
docker stop $(docker ps -a -q)
```
remove all docker containers
```
docker rm $(docker ps -a -q)
```
remove all docker images
```
docker rmi $(docker images -q)
```
port bindings of a specific container
```
docker inspect [container-id]
```

For troubleshooting: https://stackoverflow.com/questions/41208782/docker-localhost-process-not-working-on-windows .

