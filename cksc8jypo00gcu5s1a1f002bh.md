## Install And configure OpenVPN in AWS to secure your Cloud infra

## **Virtual Private Network**


> 
A virtual private network extends a private network across a public network and enables users to send and receive data across shared or public networks as if their computing devices were directly connected to the private network.


### **OpenVPN**
OpenVPN is a virtual private network (VPN) system that implements techniques to create secure point-to-point or site-to-site connections in routed or bridged configurations and remote access facilities. It implements both client and server applications.


**OpenVPN Configuration**

It Have 3 parts.


1. Launch the OpenVPN Ec2 instance in AWS

2. Configure Application in appliance via ssh

3. Configure Application  in web console

4. Download install and configure OpenVPN client

5. Test to connect your private instance via OpenVPN.



### 1. Launch the OpenVPN Ec2 instance in AWS


- 
First Launch the instance in Ec2 Service page.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628947580394/RPosV6__M.png)


- 
In the ami selection page search **openvpn** in aws market place and choose first one


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628947685031/-YN_Dj2Xh.png)


- 
Then continue in the OpenVPN vendor page . It show the cost for all types of instance and ami charge per hour. we will going to use free tier 2 user appliance.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628947847611/ROPcMwCe5j.png)



- 
In the instance type selection page choose which type of instance you want. if you have free tier eligibility choose t2 micro otherwise choose t2 nano.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628947981775/YhgYmS1kH.png)
 


- 
Leave the default option for all other settings.


- 
See in the security group section OpenVPN automatically create the security group for you.


- 
After that choose a keypair and launch the instance.


### 2. Configure Application in appliance via ssh

**Now we are going to connect our OpenVPN ec2 via ssh and configure the appliance.**


- 
Its asking license agreement give yes


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628948900632/R7dMVfAOT.png)


- 
see here we are using root user to ssh the ec2 instance.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628949047672/OLh2YKPfj.png)


- 
After that it asking many question .... you just leave the deafulat values hit enter till the end.




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628949001216/zzFzr2Hd_.png)


- 
After the configuration you must want login as openvpnas instead of root user.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628949139716/HD6g9R6U6.png)



- 
Now we are logged in as OpenVPNas (appliance default) user.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628949198641/nz1F3tIxP.png)


- 
Here we want to change the OpenVPN application user password.for that execute the below command.


- 
During this its asking password input and verification. so enter two times.


```
sudo passwd openvpn

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628949357177/BiOu--6PU.png)


- 
That's all... the shell configuration part is complete now.



> 
after that you can proceed to application configuration part.


### 3.Configure Application  in web console


- 
Now we are going to access openvpn application in browser for that enter openvpn server public ip in the below format


> 
Syntax: https://vpnpublicip:943/admin


```
https://13.233.125.209:943/admin

``` 

> 
Its looks like


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628964549801/aujPEjosO.png)


- 
Here click advanced and proceed with unsafe.



- 
Now the we are seen OpenVPN login page . enter the user name as openvpn and password you reset in previous section.


- 
After login go to configuration and VPN settings.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628964841103/r7k0mS0w5.png)


- 
Under the route settings enable the below option.


> 
Should client Internet traffic be routed through the VPN?



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628964880923/6JnrPWsUP.png)


- 
Save settings in the bottom of the page then top of the page it shows
update running sever select that.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628965007183/w4hto8Jaq.png)

**Thats all ...**

### 4. Download install and configure OpenVPN client

**Downlaod Openvpn Client and Config file
**


- 
Now we are going to download the open VPN client for our OS platform.


> 
For this open the ip with port943 in https protocol.


> 
Syntax: https://13.233.125.209:943


- 
Then login with the same credential. If you want login with different user other then OpenVPN user create it in admin console.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628965450048/SKfdlTwb6.png)

### 4. Download install and configure OpenVPN client- 
Here i am using same user for admin and user.


- 
After login to the user console it shows all the available clients for all the operating systems.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628965544677/mxDdwylts.png)


- 
I am going to download for windows client and configuration files.


**Install OpenVPN Client **


- 
After download the windows installer install it.


- 
Before enable VPN ,I want to check my public IP in browser.


> 
See this is my Public IP:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628965745644/o-emkrnjnY.png)

**OpenVPN Client Configuration
**

- 
When you open the OpenVPN client.Its asking user agreement.
Just click agree and continue.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628965833565/Ja8zZDuu-.png)


- 
After that its shows client in disconnected state.in the bottom of the client it shows one plus symbol just open it.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628966049215/KhRrRJZB4M.png)


- 
In the next screen click file and import downloaded OpenVPN config file.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628966125753/qEttZYGCh.png)


- 
And enter the password for the user.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628966160844/lK4Mi4QY7.png)


- 
After that its connected.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628967098305/qMHuGv8IX.png)


- 
Now we want to check our Public IP in browser.


> 
yea ... now the ip changed.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628967147709/b4dbY-DX2.png)

## 5. Test to connect your private instance via OpenVPN.


- 
Now we are going to test our VPN. for that we want to connect any of our ec2 instance that  have only accessible by OpenVPN Subnet.


- 
For that i will change my one of ec2 servers security group .


- 
Modify the ssh port only accessible by OpenVPN subnet.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628967903488/NpAiC-tfM.png)






- 
Now connect the server via ssh when disable the OpenVPN client.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628967867317/Iw6Oq9L8t.png)


- 
After enable OpenVPN I Have connect the server via ssh.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628967825473/xzfUxY5hY.png)



> 
**That's all guys we have successfully install openvpn and configred and tested it correctly.
**
