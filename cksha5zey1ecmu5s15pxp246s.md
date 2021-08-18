## Create the docker container using docker file

### Dockerfile

>  A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession.
So,USing that image we create the container from that.

Hi Guys Here I Am going to explain how to launch the docker conatiner from docker file.


Usually there is two ways to create docker container.

1.Pull the image from products official docker container.

2.Create the Dockerfile for customized docker container.


- 
Below i have explain the commands that are mostly used in docker file creation.




**Command	**    and **Description**

**ADD	**    =Copies a file from the host system onto the container

**CMD **   =The command that runs when the container starts ENTRYPOINT

**ENV	**    =Sets an environment variable in the new container

**RUN	**    =Executes a command and save the result as a new layer

**USER	**=Sets the default user within the container



**FROM	**=The base image to use in the build. This is mandatory and must be the 
                       first command in the file.

**MAINTAINER	**=An optional value for the maintainer of the script

**ONBUILD	**=A command that is triggered when the image in the Dcokerfile is used 
                           as a base for another image


**VOLUME	**=Creates a shared volume that can be shared among containers or by 
                           the host machine

**WORKDIR	**=Set the default working directory for the containerThe command 
                        that runs when the container starts

**EXPOSE **=Opens a port for linked containers



- 
Ok Now we are going to create one Basic Dockerfile.


> 
Dockerfile (D is case sensitive and Dockerfile is single word)

```
#get the base image from nginx official image
FROM nginx:latest

#add my index.html file from gist and paste it in nginx webroot
ADD https://gist.githubusercontent.com/yvenkets/4bc9375865f3523beed4a3f2fabbbe70/raw/bd3c36532c03fa1fe30d9457ee120af1c0e9d8fc/index.html /usr/share/nginx/html/

#give the rights to user share
RUN chmod +r /usr/share/nginx/html/index.html

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629203023623/llJsQPBUu.png)


- 
Now we are going to build the image from Dockerfile


```

sudo docker build -t nginxubunt .

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629203178481/K-kiDo2G9.png)




- 
Then we will run the container from docker image

Syntax: docker run -t -i -p hostport:containerport [imagename]

```
docker run -t -i -p 80:80 nginxubunt

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629203522696/oXEg6a7mD.png)


- 
Now the container is running


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629203575369/_LymXvT3w.png)


- 
We will check the Containers host ip in browser.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629275821512/GyuCVpKbv.png)
Yeah its working now.

Thats all Guys we create Dockerfile and build with the image from that and make a docker container successfully.

Dockerfile Link

%[https://gist.github.com/yvenkets/2e6d0fc6fff299b0e53bd72090fd85dd]

Index.html Link

%[https://gist.github.com/yvenkets/4bc9375865f3523beed4a3f2fabbbe70]
