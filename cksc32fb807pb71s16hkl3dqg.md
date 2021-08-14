## Configure Nginx Load Balancer for Node Application.

## LoadBalancer -What Is It?


> 
Load balancing is an excellent way to scale out your application and increase its performance and redundancy. Nginx, a popular web server software, can be configured as a simple yet powerful load balancer to improve your servers resource availability and efficiency.


### 1.Install node.js in our server

 
> 
If you want to deep dive on how to install node different versions. check my previous article.


%[https://venket.hashnode.dev/install-nodejs-12-14-16-versions-on-ubunturedhatcentos-and-amazon-linux]


First we want to install Node.js on our server.


```
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -

sudo apt-get install -y nodejs

sudo apt install npm

``` 
now check the node.js version.


```
node -v

npm -v

``` 
### 2.Create Sample Node Applications and test it locally

**Create Sample App 1**


- 
Now we are going to create one sample node.js app .create one file called index.js and copy paste the below code.


```

var http = require('http');
http.createServer(function (req, res) 
{
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('SHIVAM welcomes you... here after all is good.');}).listen(3000, "172.31.9.126");
console.log('Server running at http://172.31.9.126:3000/');

``` 

- 
Now we are going to run the app.


```
node index.js

``` 

you get the below output.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961854068/MkCZTKAjC.png)




- 
if you are using ubuntu in graphical mode you can check the below in browser.


```
http://172.31.9.126:3000

``` 

- 
otherwise open another terminal window check this


```
curl http://172.31.9.126:3000

``` 

- 
you got the below output



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961885925/AisF_0g-_.png)


> 
we are going to configure load balancer .so, we want create another app that's run on different port.

**Create Sample App 2**


- 
now we are going to create one sample node.js app .create one file called index2.js and copy paste the below code.


> 
note: thats the server local ip (172.31.9.126)

```

var http = require('http');
http.createServer(function (req, res) 
{
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('SHIVAM THIS IS SAMPLE APP 2');}).listen(4000, "172.31.9.126");
console.log('Server running at http://172.31.9.126:4000/');

``` 
now we are going to run the app.


```
node index2.js

``` 

you get the below output.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961950269/tmHYyQdGI.png)



open another terminal window check this


```
curl http://172.31.9.126:4000

``` 
you got the below output


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961982516/nJt7VzaOH.png)


### 3. Install Nginx service


- 
Now we are going to host the app in webserver. i will install nginx and configure reverse proxy.


- 
To Install Nginx service execute the below commands.


```
sudo apt-get install nginx -y


``` 


- 
Now the nginx server package is installed. check the server running status. also add auto-startup nginx service on system startup.


```
sudo systemctl status nginx

sudo systemctl enable nginx

``` 


- 
Check servers ip address in your browser


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628958066088/XK6_wfw4s.png)


###4. Install PM2 for continuously running our node app


- 
Now we are going to install Process manager 2 for our node js application always in running state.



```
sudo npm install pm2 -g

``` 


- 
Now we are going to add pm2 in system startup. So, run the below command.

```
sudo pm2 startup

``` 

> 
its added pm2 on system startup.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627069252916/UPVfz4jkV.png)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628958694203/oo8ybuar9.png)


- 
now we want to restart the server the setting may take effect.


```
sudo init 6
``` 




- 
now we are going to run our node .js app on pm2.


> 
Syntax : sudo pm2 start /locationto the js.file/index.js


```
pm2 start /home/ubuntu/index.js
pm2 start /home/ubuntu/index2.js

``` 

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627069411414/1G52uQdip5.png)



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628958862550/sY1J8cDPX.png)


- 
to verify our app running properly on pm2 put this command.


```
curl http://172.31.9.126:3000

curl http://172.31.9.126:4000

``` 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961398279/1IoxyKmDm.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961450646/GrRnMUuAs.png)


> 
If you want some PM2 commands refer here.


%[https://pm2.keymetrics.io/docs/usage/quick-start/]


### 5. Nginx Load Balancer Configuration



- 
Now we are going to configure nginx loadbalancer with the two running node apps.

Crate loadbalancer.conf file using the below command and add the lines in the loadbalancer.conf example section.

```
vi /etc/nginx/conf.d/load-balancer.conf 

``` 


> 
In this configuration file we will mention the two running node apps ip and port.
you want to change your own server ip and ports.

**loadbalancer.conf example 
**
```
upstream loadbalancer {
server 172.31.9.126:3000;
server 172.31.9.126:4000;
}
server {
location / {
proxy_pass http://loadbalancer;
}}
``` 


- 
Now we want to remove the default configuration symbolic link in the sites enabled location.


```
sudo rm /etc/nginx/sites-enabled/default 

``` 
                                                                                                                                                                              


- 
Finally restart the nginx service.


```
sudo systemctl restart nginx     

``` 

## 6. Final Steps - Testing


- 
Now we are going to check the servers public ip in browser.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961540347/AmpyCp9Bk.png)


- 
In first hit it shows the app 1 content in browser using port 80.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961621931/ncaFijclu.png)
 

- 
In the next hit or refresh it shows the app2 content in browser via port 80


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1628961696773/P21Gdf__y.png)


Hurray ... We are configured successfully the load balancer configuration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      