## How to deploy  your node application in web and configure reverse proxy.

### 1.Install node.js in our server

First we want to install Node.js on our server.


```
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -

sudo apt-get install -y nodejs

``` 
now check the node.js version.


```
node -v

``` 

now we are going tp create one sample node.js app .cretae one file called index.js and copy paste the below code.


```

var http = require('http');
http.createServer(function (req, res) 
{
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('SHIVAM welcomes you... here after all is good.');}).listen(3000, "127.0.0.1");
console.log('Server running at http://127.0.0.1:3000/');

``` 
now we are going to run the app.


```
node index.js

``` 

you get the below output.



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627067275618/8mGkEz1__.png)


if you are using ubuntu in graphical mode you can check the below in browser.


```
http://127.0.0.1:3000

``` 
otherwise open another terminal window check this


```
curl http://127.0.0.1:3000

``` 
you got the below output


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627067586453/on5f6Is17.png)

### 2. Install Nginx service

now we are going to host the app in webserver. i will install nginx and configure reverse proxy.

Install Nginx


```
sudo apt-get install nginx -y


``` 
now the nginx server package is installed. check the server running status. also add auto-startup nginx service on system startup.


```
sudo systemctl status nginx

sudo systemctl enable nginx

``` 

check servers ip address in your browser

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627068882370/gtphBSPiF.png)


### 3. Install PM2 for continously running our node app

now we are going to install Process manager 2 for our node js application always in running state.



```
sudo npm install pm2 -g

``` 

now we are going to add pm2 in system startup

run the belwo command.
```
sudo pm2 startup

``` 
its added pm2 on system startup.

now we want to restart the server the setting may take effect.


```
sudo init 6
``` 




![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627069252916/UPVfz4jkV.png)

now we are going to run the node .js app on pm2.

Syntax : sudo pm2 start /locationto the js.file/index.js


```
pm2 start /home/ubuntu/index.js

``` 

Output:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627069411414/1G52uQdip5.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627069432930/J1bz_8bnj.png)

to verify our app running properly on pm2 put this command.


```
curl http://127.0.0.1:3000

``` 

If you want some PM2 commands refer here.


%[https://pm2.keymetrics.io/docs/usage/quick-start/]

### 4. Configure reverse proxy for our node application

Now we are going to configure reverse proxy for node app.

first backup and remove the defaut nginx configuration files from the below path.


```
 sudo mv /etc/nginx/sites-available/default /etc/nginx/sites-available/default.orginal

 sudo vi /etc/nginx/sites-available/default

``` 

after that paste the below content on that.


```
    server 
     {                                                                                                                                                                                                                                    
        listen 80;                                                                                                                                                                                                                          
        listen [::]:80;                                                                                                                                                                                                                                                                                                                                                                                                                                                         
        root /var/www/html;                                                                                                                                                                                                                 
        index index.html index.htm index.nginx-debian.html;                                                                                                                                                                                                                                                                                                                                                                                                                     
        server_name nodev.venketraman.com www.nodev.venketraman.com;                                                                                                                                                                                                                                                                                                                                                                                                                                      

       location / {                                                                                                                                                                                                                        
       proxy_pass http://localhost:3000;                                                                                                                                                                                                   
       proxy_http_version 1.1;                                                                                                                                                                                                             
       proxy_set_header Upgrade $http_upgrade;                                                                                                                                                                                             
       proxy_set_header Connection 'upgrade';                                                                                                                                                                                              
       proxy_set_header Host $host;                                                                                                                                                                                                        
       proxy_cache_bypass $http_upgrade;                                                                                                                                                                                                   
                       }                                                                                                                                                                                                                                                                                                                                                                                                                                                             
    }  

``` 

Explain about the above syntax.

- 
in the server block mention your domain name thats is point to your server ip address.


- 
in the proxy pass line enter the port no of your node js app running port.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627073595852/TEbTVUK0c.png)

Now we want to enable the site from sites-available to sites-enabled.


```
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/

``` 

Then we are going to map our server public ip in domain name.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627073663363/dhqhFDUgR.png)


Now we are going to check the mapped domain name in browser.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627073709191/ovry7JrKQ.png)

the code that we are entered in our node app is displayed in our website.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1627073748841/x_zYQmMjO.png)

Thats all guys we are successfully covered below topics.


- 
How to run node js app and check it locally


- 
How to permanetly run node js application using pm2


- 
How to install nginx and configure reverse proxy for node application with port number.


