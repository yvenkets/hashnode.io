## Install Node.JS 12 ,14 , 16 Versions on  Ubuntu,Redhat,CentOS & Amazon linux.

# NodeJS


> 
Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code outside a web browser. Node.js lets developers use JavaScript to write command line tools and for server-side scripting—running scripts server-side to produce dynamic web page content before the page is sent to the user's web browser.

Here i am going to explain how to install different versions of NodeJS on different operating systems.

To install NodeJS  On Ubuntu using the below commands.


**Supported Ubuntu versions.
**

- 
Ubuntu 16.04 LTS (Xenial Xerus)

- 
Ubuntu 18.10 (Cosmic Cuttlefish)

- 
Ubuntu 19.04 (Disco Dingo)

- 
Ubuntu 19.10 (Eoan Ermine)
- 
Ubuntu 20.04 LTS (Focal Fossa)



### Node.js v16.x


```
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs

``` 

### Node.js v14.x


```
curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs

``` 

### Node.js v12.x


```
curl -fsSL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs

``` 


> 
To compile and install native addons from npm you may also need to install build tools.

- 
To install build essentilas


```
apt-get install -y build-essential

``` 

To Isntall node on Redhat,centos,amazon linux and


Supported Red Hat® Enterprise Linux® versions:

- 
RHEL 7 (64-bit)

- 
RHEL 8 (64-bit)



Supported CentOS versions:

- 
CentOS 7 (64-bit)

- 
CentOS 8 (64-bit)


Supported Amazon Linux versions:

- 
Amazon Linux (64-bit)

- 
Amazon Linux 2 (64-bit)


### Node.js v16.x


```
curl -fsSL https://rpm.nodesource.com/setup_16.x | sudo bash -

``` 

### Node.js v14.x



```
curl -fsSL https://rpm.nodesource.com/setup_14.x | sudo bash -

``` 

### Node.js v12.x


```
curl -fsSL https://rpm.nodesource.com/setup_12.x | sudo bash -

``` 




> 
To compile and install native addons from npm you may also need to install build tools:


- 
To Install build tools

```
yum install gcc-c++ make

``` 
OR

```
yum groupinstall 'Development Tools'

``` 

Check node version


```
node -v

``` 

its also install npm packages. so, to verify the npm version.


```
npm -v

``` 


- 
Now we are going deploy sample node application. so that we create simple index.js files using the below content.


> 
you can change the custom port number and msg to your own value.

```
var express = require('express')
var app = express()


app.get('/', function (req, res) {
  res.send('Shivam World!')
})

app.listen(8081, function () {
  console.log('app listening on port 8081!')
})

``` 


- 
Now run your sample Node Application using the below comment.


```
node index.js

``` 

check it in browser **http://localhost:8081 ** you get the message you entered in java script.






