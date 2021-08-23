## Copy AWS EC2 AMI To Other AWS Account Same Region and Other Region

# What IS AMI

Its **Amazon Machine Image**...

> 
An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.

1. Make AMI from EC2 


- 
Here i am going to explain how to Share AMI to one AWS Account to other Account.
Also explain copy the AMI one AWS Region to other Region.


> 
If You want to learn about how to create AMI from EC2. Check My previous article


%[https://venket.hashnode.dev/create-ami-from-amazon-ec2-instance]



- 
We are taking the below webserver image as AMI. See the servers public IP.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629654799206/E2PGk4ZlL.png)


- 
We will check this ip in browser.it shows my portfolio site running in this server.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629654777036/F4Y16USukc.png)


- 
I am going to take this server as AMI.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629654983792/KrlZYyxci.png)

- 
This is that webserver AMI.



- 
Now the AMI is available

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629655535019/EiqM4QP2K.png)
- 
Now we have the AMI in ap-south-1(Mumbai/India) Region.

## 2.Share the AMI to other Account

- 
This is My Source AWS Account.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629655154366/IfncDTGF5.png)


- 
This Is My Destination account


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629655392066/ObWWUlphn.png)

- 
We Will share the AMI to one of my other account.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629655587637/EeP3r6TI0.png)

- 
Click add permission and save.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629655647870/AWINJ3Ixj.png)


- 
That's all we have shared the AMI to other AWS Account.

## 3.Launch the EC2 Instance from Shared AMI Image

- 
Now we want to login to the Other AWS Account. which account we will share the AMI.


- 
In this account EC2 AMI console we can see the shared AMI image here.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629656272137/7ukqdM38E.png)


- 
Ok,Now we will going to launch the  EC2 instacne from the shared AMI.With default values.

> 
One important thing is AMI attached with SOurce account .pem Keyfile
Thats the only key file we will used to connect the instance.in this instance launch configuration we will attach our pem key file.thats not useful.


- 
I Have launched the instance. We will check the instance ip in browser to check the web server content worked after shared the AMI.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629656564491/EevcfKfUI.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629656612916/CHP9kQvxoQ.png)

- 
Yeah Its Working perfectly.

## 4.Copy AMI One region to other Region.


- 
Here i am going to explain how to copy the AMI one region to other region in the same account.


- 
First select the AMI which one want to be copy.and going to action choose the copy AMI option.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629656712782/F-L2bzExG.png)


- 
There its shows which region you want to copy the AMI.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629656828005/8GvedO1LC.png)


- 
Currently iam in ap-south-1 (mumbai/India) region.i will copy my AMI to US-East-1 Region.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629656909155/a3_TENQMG.png)


- 
Now I will Going to check the US-East-1 Region.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629657326531/tWHpj5Lli.png)

> 
Yes .its copied the AMI in this region.

**That's all Guys.**

