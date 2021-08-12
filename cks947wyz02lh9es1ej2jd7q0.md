## Install and Configure Magento on Ubuntu

**Introduction
**
> 
Magento is one of the most popular open-source e-commerce platform written in PHP powered by Zend framework. In this tutorial, you will learn the steps required to install and setup Magento on your Linux/Ubuntu 20.04 server.



- 
Every Magento version only work with some specific version of packages
like Php, Apache, Composer, MySQL and elastic search.


- 
First decide which version of magneto you are going to install. Because every version have different dependencies.

for your refence i am provide all version dependencies.

%[https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html]














# ***Ok Guys Now we start the Battle*...**  😁😁😁




### **System Requirements**

The Below version we need for Magento 2.4.0 Package.

- 
OS : Ubuntu 20

- 
Composer : 1.X

- 
Elasticsearch	: 7.6

- 
Database : MySQL

- 
PHP : 7.3, 7.4

- 
Web server : Apache 2.4


- 
Magento : 2.4.0





### **The installation have below parts**

1. Enable Swap space

2. Install Apache Web Service 

3. Create Virtual host for domain mapping

4. Install Elastic Search Service

5. Install PHP And its modules.

6. Install Composer

7. Install Mysql Server and create DB and User for Magento

8. Create Magento User account and get the credentials

9. Download the Package and compose it

10. Install the magento package


### 1. Enable Swap space
First we want to enable Swap Space for that . Basically This maganto server running many supported application's.

so we must enable swap space for that.

If you not aware how to enable swap space on linux instance check my other article.
Here. 👇


%[https://venket.hashnode.dev/how-to-enable-swap-space-on-aws-ubuntu-or-any-linux-servers]



### 2. Install Apache Web Service 


- 
To install apache run the below command.


```
sudo apt install apache2

``` 

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671460903/WSaSie-io.png)



- 
To Start the service

```
sudo systemctl start apache2

``` 

- 
To Enable on system startup

``` 
sudo systemctl enable apache2

```


- 
Enable mod rewrite module.

```
sudo a2enmod rewrite

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671589116/4R-0cPpGa.png)


- 
To edit the apache config and change the value 


```
vim /etc/apache2/apache2.conf

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671724348/k_bp_xq9_.png)


> 
Change AllowOverride value none to All


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671649735/QTmCsv8AQ.png)


- 
To restart the apache service.

``` 
sudo systemctl restart apache2   

``` 
### 3. Create Virtual host for domain mapping

In apache we will create virtual host for our magento custom domain name mapping

So we cretae the config file in the below location.

```
sudo vim /etc/apache2/sites-available/magento.conf

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671781246/qH96LkzX3.png)



and add the below content.Change your domain name in the below exapmle  in server name and server aliasis filed.

```
<VirtualHost *:80>
     ServerAdmin admin@domain.com
     DocumentRoot /var/www/html/
     ServerName mag.venketraman.com
     ServerAlias www.mag.venketraman.com

     <Directory /var/www/html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/magento_error.log
     CustomLog ${APACHE_LOG_DIR}/magento_access.log combined
</VirtualHost>

``` 
Output


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671823354/M-hQ1JvNg.png)



now we want to enable the virtual host 


```
sudo a2ensite magento.conf

sudo  systemctl reload apache2

``` 
Output:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627671862584/FzoF4CAo1.png)



### 4. Install Elastic Search Service


> 
Elastic search is the local search engine to speed up to get the product query from MySQL and displayed in web.

Here we are going to install the elastic search version7 

first add the elastic search GPG key.

```
sudo wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

- 
Then install https transport

```
sudo apt-get install apt-transport-https

```

- 
add the elastic search repository source in source list.

```
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list

```
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672198453/077eHdIrW.png)


- 
Now we are going to install and start the elastic search.

```
sudo apt-get update && sudo apt-get install elasticsearch

```
```
sudo service elasticsearch start
```


- 
Ensure your elastic search will run on system startup and restart the service.

```
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
``` 
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672306487/KE0tINYN9.png)


- 
To check the elastic search is workig properly.

```
curl localhost:9200

```
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672361214/l0v_-TnmL.png)


### 5. Install PHP And its modules.


- 
To Install php using this commands.

- 
here we install the software properties comman instalation and update the os.

```

sudo apt-get install software-properties-common

sudo apt-get update

```
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672401742/Tsz4yT93X.png)


- 
Then add the php repository and update the os.

```
sudo add-apt-repository ppa:ondrej/php

sudo apt-get update

```

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672445357/bFl5ks9wP.png)


- 
Now install the Php 7.4 and its modules.

```
sudo apt-get install php7.4 php7.4-common php7.4-xml php7.4-curl php7.4-bcmath php7.4-intl php7.4-gd php7.4-zip php7.4-mysql php7.4-soap php7.4-cli php7.4-mbstring php7.4-xmlrpc php7.4-mcrypt php7.4-gmp libapache2-mod-php7.4

```
Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672524279/f-2Hjx7hk.png)




- 
Now we want to enable Php 7.4 with apache.

```
sudo a2enmod php7.4

```

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672727454/8-Lae_k_v.png)


### 6. Install Composer

We are download the magento source files from magento website and compose it using php composer.for that purpose we want to install composer.


```
sudo apt install composer 

``` 

after the installation confirm by check the composer -v


```
composer -v

``` 
Output:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672812140/y5nXAIQxT.png)



open the php.ini file from the below location


```
sudo vim /etc/php/7.4/apache2/php.ini

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672870881/bisEKiuDe.png)

and change the below values


```

file_uploads = On
allow_url_fopen = On
short_open_tag = On
memory_limit = 512M
upload_max_filesize = 128M
max_execution_time = 3600

``` 

finally restart the apache server.


```
sudo systemctl restart apache2

``` 

check php is installed correctly .check php and its modules version.

create php.phpfile in web root. and add the below content.


```
sudo vi /var/www/html/php.php

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672918411/fem8lNTf7.png)

```
<?php
phpinfo();
?>

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627672903336/sGUVThQmO.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627326001327/8dyCvWm-q.png)

Now check browser the servers ip followed by php.php


> 
Syntax : http://serverip/php.php


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627673109349/FMHVP_WWP.png)


### 7. Install Mysql Server and create DB and User for Magento


Setting up MySQL Server


- 
To Install mysql server

```
sudo apt-get install mysql-server

```

- 
To start the mysql server

```
sudo service mysql start

```


- 
To configure mysql server

```
sudo mysql_secure_installation

``` 

 
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627673379605/HYjCh9oCl.png)



Now we are going to do MySQL  server Configuration.

- 
First it asking validate password plugin for strong password.
  
> 
No

- 
Next it asking set root password . 


> 
Type the password

- 
Asking remove anonymous user

>press y

- 
Asking Disallow root login

>press y


- 
Asking remove test databases

> 
press y

- 
Asking reload previlage to tables

> 
press y


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627673477436/KZoFfgUKS.png)



Create MySQL Database and users for Magento the following actions done here step by step.


- 
Login to the MySQL with root password.


- 
Create database named magento.


- 
Create user name magentouser.


- 
Provide the rights on magento db for magentouser.


- 
Reload privileges' and exit.


```
sudo mysql -u root -p

CREATE database magento;

CREATE USER 'magentouser'@'localhost' IDENTIFIED BY 'Vault2300';

GRANT ALL PRIVILEGES ON * . * TO 'magentouser'@'localhost';

FLUSH PRIVILEGES;

quit;

``` 
Output:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627673572239/EpdwU1nY8.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627673614781/yNNMqHvcB.png)

 ### 8. Create Magento User account and get the credentials


- 
create account in magneto portal

%[https://marketplace.magento.com/]

- 

Login to Magento Marketplace


- 
and go to the below link create access key.

%[https://marketplace.magento.com/customer/accessKeys/]

- 
genrate access keys


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627330812583/VSd9WpAQx.png)

now its ask the name just enter any name then the key generated.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627330872292/_itwMnza4.png)


## 9. Download the Package and compose it



**Now we are going to download the package from Magento repository.
**

- 
First change to Webroot folder


- 
Give the permission for the Webroot.

```
cd /var/www/html/

sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
sudo chown -Rv root:$USER .
sudo chmod -Rv g+rw .
``` 




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627675193155/cC7ogn6-P.png)


- 
Then execute the bellow command for update the composer.


```
php -d allow_url_fopen=on /usr/bin/composer update

``` 


- 
Then we are create the project via composer using the magneto online repo files.
execute the below command.

```

composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition=2.4 magento


``` 


- 
here it asks the access keys and secret keys. provide that you previously generated in magneto portal.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627675445095/OIkXJzxBs.png)


- 
After this change change your working directory as  magneto installation folder.
Change the folder and file permission using the below commands.
change the ownership of the folder to your current user.

```
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
``` 

all done. hurry...

### 10. Install the magento package

We are now in final part. Install the composed project using the below command.

you want to change the below values to your custom values.

 

> 
base URL = Ur magento hosted url

> 
db host = ur db server name

> 
db name = ur magento db name

> 
db user = db user who have the rights to access magento  

> 
db-password = ur db user password

> 
admin first name and last name = ur wish

> 
admin user name and password = ur wish

> 
admin email id = mail id for communication

> 
currency = ur customer's using  currency 

> 
time zone =ur customer time zone

> 
use rewrite = url rewrite enabled

> 
search engine name , version , host  and port number.


```
bin/magento setup:install --base-url=http://mag.venketraman.com/magento/ \
--db-host=localhost --db-name=magento --db-user=magentouser --db-password=Vault2300 \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=localhost \
--elasticsearch-port=9200
``` 

Now the installation Started....

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627738838518/4LfuME0N3.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627738872351/Q75lFp2us.png)

Here it shows the Admin URI... just copy and save it in any location. later we will access using that URI.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627738903746/DZ9XN_uyA.png)


Now we want to open the magento on browser using our custom domain name.for that we want to enable devloper mode and execute some commands.commands given below.


```
bin/magento deploy:mode:set developer 
bin/magento se:up && bin/magento se:d:c && bin/magento c:c
bin/magento cache:clean

chmod -R 777 pub/static /var generated/*

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627739729528/EOAwGnzMb.png)


- 
If you missed to copy the admin URL you can get this edit from the file


```
vi app/etc/env.php

``` 


- 
Inside this file find front name=


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627741384742/HtB86L030.png)


Finally we got the Magento site


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627741432524/sfuZRtL31.png)


Edit the URL and paste the admin URL. like below.

My Admin URL : admin_1le8jc


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627742279056/wLoAnghMOG.png)

last one thing is magneto using two factor authentication. If you are familiar with configuring relay server try magneto site for that.
otherwise using the below command to disable the two factor authentication.


```

bin/magento module:disable Magento_TwoFactorAuth

```

 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627742114816/a5ZJr_aaj.png)


- 
Now going to sign-in with your user name and password


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627742332509/9c9otlRfy.png)



- 
Now we are login here successfully


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627742491804/p6ybGWAZy.png)



- 
But here it shows some error.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627742523373/qmqoM2TYK.png)



- 
We want to re-index the magneto.


- 
For this u want to change the working directory to Webroot and then magneto folder.

ubuntu@host/var/www/html/magento$ 


```
 bin/magento indexer:reindex

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627743593656/10vIKaQ3Q.png)


- 
Now you successfully logged in your magneto server.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627745042396/GhekjgorR.png)



