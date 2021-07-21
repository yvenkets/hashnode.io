## Install Nginx server and secure your website with Certbot SSL ON Ubuntu 18

# WEB Server

A web server is computer software and underlying hardware that accepts requests via HTTP and HTTPS the network protocol created to distribute web pages and multimedia content via internet or intranet.

Some famous Web services

- Apache
- IIS
- NGINX
- Tomcat

Here i am going to explain how to install Nginx webserver and how to configure it


First update your server with latest packages.


```
sudo apt-get update -y

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626185630429/EzS04EqHC.png)


then install nginx latest version.


```
sudo apt-get install nginx -y

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626185841197/hZ-6FkLCr.png)

allow nginx required forts in firewall.


```
sudo ufw allow 'Nginx Full'

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626185964086/utF9alrBt.png)

Give folder permission to your Webroot


```
chown -R $USER:$USER /var/www/html/

chmod -R 755 /var/www/html/

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626186313684/i7zRBN6nP.png)

create index.html file in Webroot 



```
echo "Shivam" > /var/www/html/index.html
``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626186517520/blaIUSQqB.png)

Check the nginx status and restart it.


```

sudo service nginx status

sudo service nginx restart

``` 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626187065408/RZqmduIfwb.png)


add certbots PPA repository and update the os.


```
 sudo add-apt-repository ppa:certbot/certbot -y

sudo apt-get update -y

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626187720294/j2GBmEbPq.png)

Now we are going to install nginx certbot package.


```
sudo apt install python-certbot-nginx -y

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626187921551/6mbymOiKw.png)

after that we are going to get ssl using certbot

Syntax sudo certbot --nginx -d www.domainname.com -d domainame.com 

```
sudo certbot --nginx -d www.try.venketraman.com -d try.venketraman.com 
``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626188797746/eKsupfIoo.png)

first it asks mail id for renewal notification

after that its asks agree the license agreement


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626189191922/o515VTMO_C.png)

after that its asks http to https redirection 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626189384787/iZxZlYr9i.png)

Give no 2 for certbot auto redirection

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626189903945/v3z13ze9J.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626189992669/J-2Jn6Gx0.png)

now you can check your website is secured with ssl.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626190135153/ON2qqmpwq.png)

additionally you can check your certificate trust level in ssl labs website.

 [SSLLabs](https://www.ssllabs.com/ssltest/) 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626190378341/uXquBjJ2B.png)


In this article i have explained how to install nginx and how to configure ssl .