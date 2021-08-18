## Install a Service or Application with User Data in AWS EC2

### User Data

 
> 
When you launch an instance in Amazon EC2, you have the option of passing user data to the instance that can be used to perform common automated configuration tasks and even run scripts after the instance starts.




     

**You can pass two types of user data to Amazon EC2: **

- 
shell scripts 
- 
cloud-init directives.


> 
 You can also pass this data into the launch wizard as plain text, as a file (this is useful for launching instances using the command line tools), or as base64-encoded text (for API calls).

### 1. Launch Windows instance with user data

 
- 
We will going to launch the windows instance with the user data.The user data will install the IIS Serivce at system launch time.


> 
If you not aware how to launch your AWS Windows EC2 Check my previous article. 👇

%[https://venket.hashnode.dev/launch-your-first-aws-cloud-ec2-server-windows]


- 
In the Configure instance section at the bottom you have seen user data filed. You can enter your custom user data with powershell tag.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629286699110/l1l5JnDtB.png)
- 
I will Put IIS Instaltion commands with powershell tag.


```
<powershell>
Install-WindowsFeature -name Web-Server -IncludeManagementTools
New-Item -Path C:\inetpub\wwwroot\index.html -ItemType File -Value "Shivam open knowledge center welcomes you" -Force
</powershell>

``` 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629287075612/yf3GLCIJk.png)


- 
**Now we will check the servers public ip in browser.wheteher webservice installed properly.
**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629287124829/HIP-ge2rj.png)

### 2.Launch Amazon Linux2 instance with user data


- 
We will going to launch the Amazon instance with the user data.


- 
The user data will install the Webservice (httpd) at system launch time.


> 
If you not aware how to launch your AWS Linux EC2 Check my previous article.👇

%[https://venket.hashnode.dev/launch-your-first-aws-linux-instance]

- 
In the Configure instance section at the bottom you have seen user data filed. You can enter your custom user data with Bash sheel script.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629295071873/xl7auSNqO.png)

- 
I will Put the below httpd Installation Userdata as a bash script.


```
#!/bin/bash
yum update -y
yum install httpd -y
service httpd start
chkconfig httpd on
echo "<h1>Shivam Corp Welcomes You</h1>" > /var/www/html/index.html

``` 


- 
**Now we will check the servers public ip in browser.wheteher webservice installed properly.**
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629295197704/97fR-gCJx.png)

### 3. Launch Amazon Ubuntu instance with user data


- 
We will going to launch the Ubuntu instance with the user data.


- 
The user data will install the Webservice (Nginx) at system launch time.


> 
If you not aware how to launch your AWS Linux EC2 Check my previous article.👇

%[https://venket.hashnode.dev/launch-your-first-aws-linux-instance]

- 
In the Configure instance section at the bottom you have seen user data filed. You can enter your custom user data with Bash shell script.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629294562176/0X5cuB3zN.png)
- 
I will Put the below Nginx Installation User data as a bash script.


```
#!/bin/bash
apt update
apt install -y nginx
systemctl enable nginx
systemctl restart nginx
echo "<h1>Shivam Corp Welcomes Youu</h1>" > /var/www/html/index.html

``` 




- 
**Now we will check the servers public ip in browser.wheteher webservice installed properly.**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629294796522/1fC0p9YP8.png)
