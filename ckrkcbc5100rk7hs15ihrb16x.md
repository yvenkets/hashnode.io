## How to install GUI For Amazon linux2 and access the GUI Session

Here i am going to explain how to install amazon linux 2 GUI and access the Instance GUI Mode

Amazon linux is the famous cloud linux os distibution its also available now for on-permises.

If you have know how to launch the linux instance continue this article.or have doubt on it. read my below article.


Here i am going to install MATE Desktop environment package.

connect your instance through ssh. and update the OS.


```
sudo yum update -y

``` 
### 1. Install MATE Packages and configure

now we are going to install MATE Desktop package its part of amazon linux extras package.


```
sudo amazon-linux-extras install mate-desktop1.x -y

``` 
all the MATE packages installed .

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627199216755/nDOt63423.png)

now we are going to set MATE Desktop is default desktop for all the users .


```
sudo bash -c 'echo PREFERRED=/usr/bin/mate-session > /etc/sysconfig/desktop'

``` 
optional

If you want set this MATE Desktop environment for only ec2-user.


```
echo "/usr/bin/mate-session" > ~/.Xclients && chmod +x ~/.Xclients

``` 

### 2. Install TightVNC server and configure

  Install TigerVNC packages:


```
sudo yum install tigervnc-server

``` 
Result will be


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627199800998/kXlTHumCw.png)

now we are going to configure vnc password for authentication.


```
vncpasswd

``` 

Its asking vnc remote access enter it.
again it asking vnc view only password set it.

Output:



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627200877149/OwBI-B9W-.png)
 
Optional

If you want to access the server via vnc viewer only once execute this


```
vncserver :1

``` 
if you want  always start the VNC Server at boot time.

execute this


```
sudo cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@.service

``` 

Use sed command to replace ec2-user where USER in the config file .



```
sudo sed -i 's/<USER>/ec2-user/' /etc/systemd/system/vncserver@.service

``` 

reload the system Damoen


```
sudo systemctl daemon-reload

``` 
 now we want to enble the seervice for sysyem start up.


```
sudo systemctl enable vncserver@:1

``` 
 and start the service



```
sudo systemctl start vncserver@:1

``` 
finally reboot your instance.



```
sudo init 6

``` 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627209715894/0fUl_0kLv.png)

### 3. install tight vnc viewer on your desktop and configure

First we want to download vnc viewr fromthe below link and install it.


%[https://www.realvnc.com/download/file/viewer.files/VNC-Viewer-6.21.406-Windows.exe]

then connect our ec2 instacne with SSH Client with the below command.

Use the -L parameter to enable port forwarding.
Replace PEM_FILE with the path for your private key. 
Replace INSTANCE_IP with your instance's public or private IP


```
ssh -L 5901:localhost:5901 -i aws.pem ec2-user@13.233.250.154

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210334146/ZfLSLNRfP.png)

now your made the connection with your instance in cli.

now we are going to open our server via vnc viewer.

open vnc viewer and enter in the hostname filed.


```
localhost:1

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210464274/vQX_0kVVo.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210514892/7wb5TimXm.png)


enter the created vnc password in password field and connect it.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210547396/HzmbLtGvZ.png)

Ye , Finally we connected our Amazon linux 2 instance in GUI Mode.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210663494/ifHJ5MZnV.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210711940/xkzcR40FW.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627210739750/lcdTXqHvP.png)


its done.

Optional 

### 4.Install chrome browser



```
sudo amazon-linux-extras install epel

sudo yum install chromium

``` 
