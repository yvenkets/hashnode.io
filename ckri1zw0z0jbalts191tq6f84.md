## How to configure Multisite in Nginx on Ubuntu 18

Nginx is a famous web server package. Here i am going to explain how to install nginx and configure multiple site on that single server.

First we are going to upgarde and update the server.


```
sudo apt-get update -y
sudo apt-get upgrade -y

``` 

after that instll nginx package


```
sudo apt-get install nginx

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626896057635/Cx8xZ60lg.png)

now going to check servers public ip in browser . you can see the default nginx page.



> serverip


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626896106249/drlpuTi7m.png)



Some commands to check status of nginx service

**To Start naginx**

```
sudo service nginx start

``` 

** To Stop nginx**

```
sudo service nginx stop

```

**TO Restart nginx**

```
sudo service nginx restart

```
To check nginx status


```
 sudo service nginx status

``` 

enable nginx auto start on system startup.


```
sudo systemctl enable nginx

``` 

### 2.Configure Nginx 

now we are going to create folder for our website 1 in webroot and change the ownership for that folder.


```
sudo mkdir -p /var/www/html/web1

sudo chown -R $USER:$USER /var/www/html/web1

``` 
output

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626896882049/rRU09qNqH.png)

create the index html file in webserver 1 root path and some content on that file.


```
echo "<img src="https://loverays.com/uploaded_images/Shiva_612.jpg" alt="shivam" width="460" height="500">" | sudo tee -a /var/www/html/web1/index.html

``` 

now we are going to create folder for our website 2 in webroot and change the ownership for that folder.


```
sudo mkdir -p /var/www/html/web2

sudo chown -R $USER:$USER /var/www/html/web2

```

create the index html file in webserver 1 root path and some content on that file.


```
echo "<img src="https://thenewsqube.com/wp-content/uploads/2020/11/Athulya-Ravi-06.jpg" alt="shivam" width="460" height="500">" | sudo tee -a /var/www/html/web2/index.html

``` 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626898720328/7JIdJhxUw.png)


now we are going to create the website 1 configuration file in nginx sites availabe folder and add the below content on it.


```
sudo vi /etc/nginx/sites-available/web1.conf

``` 


```
server 
{
listen 80;
listen [::]:80;

# below line is website 1's webroot 

root /var/www/html/web1;



#what is your index file name mention here ex: login.html

index index.html index.htm index.nginx-debian.html index.php login.html;

# this Server name block you want to mention your domain name

server_name web1.venketraman.com www.web1.venketraman.com;

}

``` 
output


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626900485997/-NARcosNr.png)


do the same steps for website 2

now we are going to create the website 2 configuration file in nginx sites availabe folder and add the below content on it.


```
sudo vi /etc/nginx/sites-available/web2.conf

``` 


```
server 
{
listen 80;
listen [::]:80;

# below line is website 2's webroot 

root /var/www/html/web2;



#what is your index file name mention here ex: login.html

index index.html index.htm index.nginx-debian.html index.php login.html;

# this Server name block you want to mention your domain name

server_name web2.venketraman.com www.web2.venketraman.com;

}

``` 
output

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626900564055/8jXKGpOdj.png)
Enable the websites

now we are going to enble the websites which is we want to publish to public.

enable website 1


```
sudo ln -s /etc/nginx/sites-available/web1.conf /etc/nginx/sites-enabled/

``` 

enable website 2

```
sudo ln -s /etc/nginx/sites-available/web2.conf /etc/nginx/sites-enabled/

``` 

 after do the necessary changes you want to modify the default web root permission.


```
sudo chmod -R 755 /var/www/html/

``` 

now we are going to verify our configuration made on nginx is corrcet.


```
nginx -t

``` 

output


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626900677995/gGeiumf_D.png)

After all the changes restart the nginx service and verify the nginx service status or in running status.


```
sudo service nginx restart

sudo service nginx status

``` 
output


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626900710346/wTNAZjfIl.png)

now we are going to map our servers public ip to our domain name .

i am using GoDaddy for domain registrar.

i have created two a records web1 and web2 with same ip address.

Web1

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626900814265/kKQEqbLcq.png)

web2

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626900864411/ICfUTSOX6.png)




now we are going to check the websites are working.

web1


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626901092639/y03bbhsmv.png)

web2


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626901621189/MQ_B5Eq3l.png)

Hurry.. we are successfully configured our multisite nginx websites .