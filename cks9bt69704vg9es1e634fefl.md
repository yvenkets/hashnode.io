## Install and Configure Docker on Ubuntu

## What is Docker ?


> 
Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.

### Docker vs Virtualization  comparison diagram

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628795402384/1Q5AV3Bx_.png)


- 
In this post i ll explain how to install docker and configure it


- 
First we want to remove the old version of docker


```
 sudo apt-get remove docker docker-engine docker.io containerd runc

``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798031523/GzuRjG3qM.png)

- 
Then update the os

```
 sudo apt-get update

``` 

- 
Install the dependencies

```
 sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

``` 
Output:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798096629/h2sG-n1QH.png)

- 
Add docker official GPG key 


```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798151865/ENLN09Zaa.png)

- 
Use the following command to set up the stable repository.


```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

``` 
Output:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798194045/b6tc3X1PW.png)

- 
Again update the server


```
 sudo apt-get update

``` 


- 
Install Docker Engine



```
sudo apt-get install docker-ce docker-ce-cli containerd.io

``` 
Output:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798310101/4ra_excNF.png)


- 
Now we are add our user in Docker service group. So that we will execute the docker command with out root access or sudo access.

First check the docker group is already created.


```
sudo cat /etc/group 

``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798612365/SvOeU8HZx.png)

- 
Now you can see the docker group created inn the last few lines entry. if its not there create the group docker.


```
sudo groupadd docker

``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798637647/HN2Qqt4dV.png)

- 
After that add your non root user to that docker group.


> 
Syntax: sudo usermod −aG docker [non−root user]



```
sudo usermod −aG docker ubuntu

``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798669527/caSUnHf_Y.png)

- 
After this enable the docker service on system startup.



> 
Enable Docker service on system startup.


```
 sudo systemctl enable docker.service
 sudo systemctl enable containerd.service
``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798714105/QFUzqCVEV.png)

- 
To take effect all the configuration changes restart the server.


```
sudo init 6

``` 

After that system restart we want to check docker running properly. so that we want to run 
sample docker container. Docker provide hello world container for testing purpose.


```
 sudo docker run hello-world

``` 
This command downloads a test image and runs it in a container. When the container runs, it prints a message and exits.

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628798450340/8n8lMD-Ch.png)

**Thats all guys... we are successfully installed docker.
**

