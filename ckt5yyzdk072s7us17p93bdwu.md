## Modify Your EC2 Instance Volume Size (both windows and linux)

**Amazon EBS volumes
**


> 
An Amazon EBS volume is a durable, block-level storage device that you can attach to your instances. After you attach a volume to an instance, you can use it as you would use a physical hard drive. EBS volumes are flexible. 


- 
You can increse or decrese the size of a volume.also you can attach and deatch the volume. so that you can simply add the many volumes to once instance.

**Here i am going to explain how to Increse the volume size in WIndows and Linux ec2 instances.**

### 1.Resize your EBS volume size for the Linux EC2 instance



- 
Below images show my Linux instance and its volume size.it have 8 GB of space.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630742456512/1fuspJ0zJ.png)


- 
I am showing the volume size and available space inside the linux os using ** df -h **command

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630742517655/SoR9YmXKu.png)


- 
This volume have 8GB of total spcae ,used space is 1 Db then available space is 6GB


- 
Select the ec2 instacne which you want modify the volume size and going to select storage section and choose which volume you are going to modify.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630768196566/y-8ZBc3Ff.png)

- 
Select the volume and modify
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630742562566/yJlgzxQlz.png)


- 
Provide the new volume size and modify
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630742607204/FBY4PN9QK.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630742625250/-3h-Lm_Fq.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630742678880/s5EfiKAa5.png)



- 
It will take some time to modify the instance volume size.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630743052933/YORntD1lI.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630751515162/TDrSEhP_p.png)


- 
After getting the in-use action getting as green color you modification is done.


- 
Now we are going to check the volume size inside the Linux OS.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630753523894/4khmq40gL.png)


> 
See now the size has been changed.

- 
Total volume size = 16 GB

- 
Used size = 1 GB

- 
Available space = 14 GB

### 2.Resize your EBS volume size for the Windows EC2 Instance


> 
Do the Same steps which we have done for linux

- 
This  windows instance volume have 30GB of total spcae .
we are going to modify the volume size.just select the volume.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630754492745/LC9QgmnnL.png)


- 
Select the volume and modify
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630754512211/rvzUsNR4l.png)

- 
Provide the new volume size and modify

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630754543680/htllHjNMn.png)


- 
After getting the in use as green color you modification is done.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630754583487/4RigKcd5r.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630759856351/LJJeUx3_jb.png)


> 
After increase the volume size we must want to login to the windows instance via rdp.


- 
Open diskmanagement console 


> 
Run-> diskmgmt.msc

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630760189344/EqhVJv6EB.png)


- 
To extend the disk space in drive right click on the newly allocated space and select extend volume.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630760506493/Cd3BY6veV.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630760588637/1j6N-FtyA.png)

**Now our Volume size is increased inside the os.**