## Jenkins Server installation

Jenkins is an open-source server that is written entirely in Java.It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery. It is a server-based system that runs in servlet containers such as Apache Tomcat. 
It lets you execute a series of actions to achieve the continuous integration process, that too in an automated fashion.

Jenkins facilitates continuous integration and continuous delivery in software projects by automating parts related to build, test, and deployment. This makes it easy for developers to continuously work on the betterment of the product by integrating changes to the project.

Here we are i will explain how to install Jenkins server in Amazon Linux 2 / centos.



First we want to install Java 1.8 stable verion on that server. bcoz jenkins developen and run in JVM.


```
yum install java-1.8* -y

``` 

Next add the java path in bash profile file.

So first execute the below command to add java path in bashrc profile.


```
echo "JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::")" | sudo tee -a /etc/profile

source /etc/profile

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375163882/AuAeuBvIb.png)

and verify the java path is added in bashrc file using the below command


```
echo "$JAVA_HOME

``` 

its shows the java path


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375276863/e1cocpJu2.png)

now we are going to add jenkins repo to our server.


```
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375460895/o9sCGx89l.png)

then import jenkins rpm key 


```
 rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375502240/FMLALD62K.png)

now we are going to install the jenkins package


```
  yum install jenkins -y

``` 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375587485/ZM9mOm04G.png)


Now we are going to check the Jenkins service status and start it.


```
service jenkins status

service jenkins start

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375708786/zjGDslnyE.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626375723585/QsDBe03qq.png)

now we are going to open the jenkins server in browser.
confirm you are open your server 8080 port in firewall.

open your servers ip address with port no in browser.

Syntax : 123.456.345.234:8080


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376008203/5XjiOHiCg.png)

in that screen your seen reset jenkins admin password. 

in the server terminal you can get the onetime password for jenkins using the below command.


```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword 

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376123184/vmHS7aq1H.png)


paste the password on that page and initialize server configuration wizard.

here you can choose install suggested plugins.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376232065/RvxtGuBJZ.png)

after that it will install Jenkins suggested plugins automatically.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376319470/kfdpT9qbY.png)

After that you want to create your admin user and password for Jenkins.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376494475/Lv_O3dP36.png)

If you have any custom domain name to map to your ip instead of ip address mention it here.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376595771/WuQwB1tjk.png)


now we are going to start jenkins.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626376624840/mCP3gqXZ9.png)

The Jenkins installation part is done. I will post basic configuration part in my next blog post.

