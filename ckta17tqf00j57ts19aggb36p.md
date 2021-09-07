## Create Launch template for AWS EC2 - Simplify your work

### Launch Templates


> 
A launch template is similar to a launch configuration, in that it specifies instance configuration information. It includes the ID of the Amazon Machine Image (AMI), the instance type, a key pair, security groups, and other parameters used to launch EC2 instances. However, defining a launch template instead of a launch configuration allows you to have multiple versions of a launch template.

** Here I am going to explain how to create the Launch template.**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631016496639/l3iN2Fp1W.png)
- 
Open EC2 Console in AWS. then goto launch template under instance section.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630595726353/7pFj9-HeA.png)



- 
Create the launch template

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630595751075/CsUcQnw-wK.png)


- 
Enter the launch template name and version description. Then add the template tag.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630595844784/ip2miJpoG.png)

- 
Select the AMI Name from the drop down.here you can select any operations system image that is available in amazon market place.you can also choose your own custom image.

- 
Then select the Instance type.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630595928204/UvBDf4TW5.png)


- 
Select your key pair ,VPC and Security Group in this screen.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630595988902/UARKuwH8O8.png)

- 
Select the Volume size and type.if you want additional volume you can add here.
then click advanced details. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596037287/vJXIobi67.png)


- 
Enter Your custom User data here. I have enter the userdata to install the nginx webservice.

```
#!/bin/bash
apt update
apt install -y nginx
service nginx restart
systemctl enable nginx
echo "<h1>Hello Shivam</h1>" > /var/www/html/index.html

``` 

- 
Then finally create launch template.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596194679/Ki8dQl_-y.png)


- 
Now we can see the created launch template in the launch template console.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596262413/OWjpJR0BI.png)

- 
In the EC2 dashboard launch instance option drop down we can see the other option launch instance from template.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596300302/OTlKBjksF.png)


- 
Select the Launch template you want to launch and select the version also.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596323167/nfsbCFbaM.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596352507/M6qnVJgAM.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596372759/WmcKxldNY.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596398834/q07585o9d.png)


- 
Now you can see the Instance in the EC2 dashboard.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596439161/zg1AQX4ZB.png)

- 
Just check the servers public IP in browser.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596475440/O_4XbNJQa.png)


- 
See the content that you are entered in user data.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1630596552054/0gOS7zF-0y.png)
