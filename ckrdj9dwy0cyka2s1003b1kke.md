## Install LAMP Server and configure Wordpress site on it

LAMP Server is a famous web server model.

Lamp server is 

L = Linux
A = Apache
M = Mysql
P  = Php

It means what is the OS platform you going to install all the applications

**L = Linux**

What is the web service package you going to use

**A = Apache
**

What is the Database your going to use to store your data

**M = MySql**

What is the Application you going to write the code and compile

**P = PHP**

Here i am going to install lamp setup in ubuntu server and configure WordPress on it.

First logn to root in terminal


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626790027482/Dkk4UOYQC.png)

then update and upgrade the server


```
apt update && apt upgrade

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626790119928/caW0PRYD9.png)


### Step 1: Install Apache

We are install the apache web service now.


```
apt install apache2

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626790256780/xzkzvrOxrF.png)

Now check the apache 2 service and set it to enable on startup


```
systemctl status apache2

systemctl enable apache2.service 

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626790615305/myClhF8rp.png)

Now check your servers ip address in web.


> http://youripaddress

**Output**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626790703323/cFnKNC4WL.png)

## Step 2: Install MySQL

Now we are going to install mysql and configure that.


```
apt install mariadb-server mariadb-client

``` 

**Output**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626790886487/pgzRIckId.png)

Now we are going to configure mysql.


```
mysql_secure_installation

``` 

first step it asking current root password . just 

**press enter
**

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626791060323/ourHOitvV.png)

then its asks set root password

**Press Y**

and enter your password


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626791251477/1R_ATkjhI4.png)



then its asks remove anoynumos users

**press Y**

Disallow root login remotely

**press Y**

Remove test database and access to it

**press Y**

Reload privilege tables now


**press Y**


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626791407616/rVdPr2Wxy.png)

now the database instalation part is done.

### Step 3: Install PHP

Now we are going to install php.


```
apt install php php-mysql

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626791507037/mlQgnFiEs.png)

to confirm php is installed and work properly we are going to create one php file(test.php) in the below path


> 
/var/www/html/


```
echo "<?php phpinfo(); ?>" | sudo tee -a /var/www/html/test.php

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626792611433/gN3EuHbkl.png)
and check it in browser the below syntax

http://serverip/test.php

output

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626792710096/5Jzu8lKfc.png)




### Step 4: Create WordPress Database

we are going to create database for WordPress on MySQL.


```
mysql -u root -p

``` 

output

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626793943437/ZCd73C4mNe.png)

Create a database for our WordPress .


```
CREATE DATABASE wordpress_db;

``` 

create the database user with password

```
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'password';

``` 
and grant permission to the database to the user

```
GRANT ALL ON wordpress_db.* TO 'wp_user'@'localhost' IDENTIFIED BY 'password';

``` 
Output

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626794236798/Y4sjnlMGe.png)

finally flush the privilege and exit hte mysql application

```
FLUSH PRIVILEGES;

Exit;

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626794861057/thvNwiJ2E.png)



### Step 5: Install WordPress

change the tmp directory and download the package from the below URL.


```
cd /tmp && wget https://wordpress.org/latest.tar.gz

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626795002450/YdWalWapV.png)

uncompress the tar file using the below command


```
tar -xvf latest.tar.gz

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626795131719/_pbIEm3Ak.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626795087071/usCXyzb57C.png)


Copy the wordpress folder to this path /var/www/html/ .


```
cp -R wordpress /var/www/html/

``` 

change ownership of ‘wordpress’ directory uing this command


```
chown -R www-data:www-data /var/www/html/wordpress/

``` 

change the files permissions for the wordpress folder


```
chmod -R 755 /var/www/html/wordpress/

``` 
cretae upload folder in worpress directory and change its permission


```
mkdir /var/www/html/wordpress/wp-content/uploads

chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads/

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626796030661/EO0gJWArW.png)

now we are going to install wordpress application via browser.

syntax  http://serverip/wordpress

choose your language and  continue

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626796143130/LMQmhCPH5.png)





now start the instalation


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626803603593/YWHKedM0Q.png)



Fill the fields order wise in 
  
database name = database youhave create in MySql

username =  enter the dbuser you have created

Password = enter the db user password

databasehost = enter the db server ip (mostly localhost)

table prefix = wp_ (enter the client or product name first twoletters followed by_)

then click the submit button.





![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626813319045/xnKYiquqi.png)

then run the instalation.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626813353251/cLfWt-sMK4.png)




now you are seeing the welcom screen. enter the site credentials,username,password and email.

and finish the installation.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626813526917/_kOyhz01b.png)






then click the login button and enter your credentials to enter the site.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626813580115/1VKHUggrW.png)






![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626813638383/3tCRG5w9E.png)

now you are successfully configured your wordpress instalation and entered the site.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626813711963/tGcjB4wiz.png)
