# WebApi

## This is web api repository storing web api code to resolve and print out current ip address of www.google.com, www.amazon.com, and www.facebook.com with json format.

For demostration: a VM linux machine with docker installation is used. Following steps should be done on the VM to get expected result

Run following commands on the VM:
```
#create base folder
mkdir /demo & cd /demo
#cloning source code from github
git clone https://github.com/qtanit87/WebApi.git 
```

**1. Create a Java console application that resolves and prints out the current ip addresses resolved from www.google.com, www.amazon.com, and www.facebook.com.**

Run following commands on the VM:
```
#move to Dockerfile folder of java app
cd /demo/WebApi/Dockerfile/app
#build image for java app console
docker build --tag appimage .
#run container with java app image
docker run -dit --name app appimage
#check result by accessing console log of the container
docker logs app
#result example:
Public IP Address of: www.google.com/142.251.41.36
Public IP Address of: www.amazon.com/18.67.16.74
Public IP Address of: www.facebook.com/157.240.26.35 
```

**2. Create a Dockerfile that builds and runs web api inside of a rockylinux image**

Run following commands on the VM:
```
#move to Dockerfile folder of web api app
cd /demo/WebApi/Dockerfile/webapi
#build image for web api app
docker build --tag webapiimage .
#run container with web api image (mapping localhost to the docker host)
docker run -dit --net="host" --name webapi webapiimage
```

**3. Create a NGINX config file and docker container so that we can host the app locally via http://localhost/ on port 80**

Run following commands on the VM: 
```
#move to Dockerfile folder of nginx app
cd /demo/WebApi/Dockerfile/nginx
#build image for nginx service
docker build --tag nginximage .
#run container with nginx image (mapping localhost to the docker host)
docker run --net="host" --name nginxproxy  -d nginximage
#mapping port 80 from VM to the host machine and access following page for the result
http://localhost/MyWebSite/rest/hosts
```

## Future improvement
- upgrade java console class for looping code
- using jenkins pipeline for automatation (build and deploy)

