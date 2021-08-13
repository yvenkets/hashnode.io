## Docker Most Used Commands.

In this article I am going to explain most using docker commands.


> 
If you want to know how to install docker check my previous article.


**1**. To Check the installed docker version


```
sudo  docker --version

``` 


**2 **. To download the image from docker hub.its not need yout docker hub login.
its pull public images only.


> 
syntax : docker pull [imagename]

```
sudo docker pull httpd

``` 
**3**. TO list out all the locally available lmages


```
sudo docker images

``` 

**4**. To view all available local docker images

```
sudo docker images -a

``` 

**5**. To run the container from available images


```
sudo docker run -it  --name [container_name]  [image_name] /bin/bash
``` 

**6**. To list out running containers


```
sudo docker ps

``` 

**7**. To list all the docker containers running/exited/stopped with container details.

```
sudo docker ps -a

``` 

**8**. To Login to the docker container


```
sudo docker exec -i -t [container_name] /bin/bash

```

**9**. To Copy all files from current location to the docker container


```
COPY . /usr/share/nginx/html/

``` 


**10**. To Copy files from container to base host os

```
sudo docker cp 09ca6feb6efc:/usr/local/apache2/logs/httpd.pid /home/ubuntu/

``` 
**11**. To start the container 


```
sudo docker start [container_name]

``` 

**12**. To stop the container


```
sudo docker stop [container_name]

``` 

**13**. To restart the conatiner


```
sudo docker restart [container_name]

``` 

**14**. To stop the container forcefully

``` 
sudo docker kill [container_name]

``` 

**15**. To stop and remove all running containers.


```
sudo docker rm $(docker ps -a -q)

``` 

**16**. To remove the docker container


```
sudo docker rm  [container_name]

``` 

**17**. To remove docker images


```
sudo docker rmi [image_name]

``` 

**18**. To remove all the docker images

```
sudo docker rmi $(docker images -a -q)

```

**19**. To login to the docker hub / its asking username and password for docker hub.

```
sudo docker login

```
**20**. TO tag the image

sudo docker tag imagename dockerhubname/new_or_same_imagename

```
sudo docker tag nginx_lb 589589/nginx_lb   

```

**21**. To push the image to docker hub


> 
syntax: sudo docker push dockerhubname/new_or_same_imagename

```
docker push 589589/nginx_lb

```

**22**. To Pull public image from docker hub

```
docker pull 589589/nginx_lb

```

**23**. To commit the docker image

Actually if make any changes to the container and wan to create new image from that ,the commit option is for that.


```
sudo docker commit [CONTAINER_ID] [new_image_name]


```
**24**.  To check the specific container login
 

``` 
 sudo docker logs [conatiner_name]

```  

**25**. Get detailed information about docker installed on the system including
the kernel version, number of containers and images, etc.

```
sudo docker info

``` 