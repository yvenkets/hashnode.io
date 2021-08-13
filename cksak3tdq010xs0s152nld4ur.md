## Create AMI from  Amazon EC2 instance

What IS AMI

Its **Amazon Machine Image**...

> 
An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.


 
**An AMI includes the following:**


- 
One or more Amazon Elastic Block Store (Amazon EBS) snapshots, or, for instance-store-backed AMIs, a template for the root volume of the instance (for example, an operating system, an application server, and applications).


- 
Launch permissions that control which AWS accounts can use the AMI to launch instances.


- 
A block device mapping that specifies the volumes to attach to the instance when it's launched.


**Here i am going to explain how to take AMI of the running server.
**


- 
For example the below server is a webserver.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628851853639/e7Eo679fyY.png)




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628851897916/CYh651ej2.png)


- 
See here the servers public ip shows the website content.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628851924096/wKn4LKEmy.png)



- 
Now we are going to take backup of the webserver as a image backup.



- 
Select the instance and going to actions -> select images and templates in the drop down menu.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628852016024/2Ply0z5em.png)



- 
Then create the image.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628852125865/rrtX4aunv.png)



I Have explaining about the below image.

- 

* Steps 1 & 2* Here we first give the image name and image description.


- 
*Step 3* if you want take image while server is running and you dont want to reatsrt just enable the option. no reboot.
if you want increse the root voulme size of server in image backup,you can increase it here.


- 
*Step 4* Then verify the delete on termination option. if you enable means volume will be delete when you terminate the server.


- 
*Step 5 *finally create image.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628863971435/kRTIrTxYW.png)


So now the AMI image is created. you can view it on in the left side pane of ec2 service page.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628866449010/9S_BS-IId.png)


- 
Now we are going to restore the AMI.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628866528506/gSQfHxtsW.png)



- 
Lave the default options and launch.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628866578031/lU0hhGa0X.png)


- 
Finally it asks which key pair you going to inject in the imported ami server image.


- 
Actually if you launch the server from AMI no value for newly attached key.


- 
For security reason amazon only consider the key pair alredy attached in servers. not a new one.
So you can use your previous key pair for connect the AMI Imported instance.


- 
Now the instance is launched. we will check the web server is working using the servers public ip.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628866950901/JfL3OTq8m.png)

**Yeah .... the sites is working..
**
So our AMI Creation and restoration is working perfectly.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628867026752/6jGScXW7x.png)


### To Remove the AMI


- 
The other one thing is how to remove the ami....


- 
To remove the we first want deregister the ami and deltete the snapshot.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628867750539/lyzpzBJR7.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628867703354/GCa_sjSUf.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628867797745/qSBtujdJu.png)

**That's all Guys...**