## Install NagiOS Monitoring tool in Amazon Linux 2

Nagi OS is the popular monitoring tool in the IT Support platform tools.
its monitoring everything in the every devices under the network.it support the below protocols.

Nagi OS License model.

Here i am going to explain how to install Nagios packages and it plugins on the server and configure it.

First we are add the amazon Linux extras epel repository to install Nagios package.


```
sudo amazon-linux-extras install epel -y

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626542291057/6MYYltnjK-.png)


install the nagios packages and plugins


```
sudo yum install nagios nrpe nagios-plugins-all
``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626542460083/iM8KD8kKV.png)

set auto start in system startup for Nagios service .


```
sudo chkconfig -–level 3 nagios on

``` 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626542617564/91cstFeRz.png)


install http Service and set AutoStart for system startup
restart the http service

```
sudo service httpd start
sudo chkconfig httpd on

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626542820288/DL6v8wQ7D.png)



install the php service


```
 sudo yum install php

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626542885059/QqgxasWzc.png)


edit contact configuration file in nagios and replace your contact mail id which is received the alert notification.


```
sudo vi /etc/nagios/objects/contact.cfg

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543071216/fAUA8k_8n.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543249617/ETZnCcz5c.png)


after the edit check nagi os confiuration file with default nagi os configuration file.


> 
```
sudo /usr/sbin/nagios -v /etc/nagios/nagios.cfg 
``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543450639/1N9vDuD0-.png)

re-start the nagi os service.

 
```
sudo service nagios start

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543601421/S_IPksew9.png)

now open nagi os in web console. using the below syntax.

Syntax Server IP/nagios


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543661272/5jrADixDj.png)

the default user name and password is nagiosadmin


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543725063/HUP0NYTkX.png)

in defualt nagi os autometicaly check the nagios server health status and show in the console.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626543767673/91jV4cVzV.png)

 



